
    b-datepicker — customized calendar/datepicker control.
    Working example: http://silkleo.ru/fun/b-datepicker/



    Goods:

    — no external libraries required (pure JavaScript);
    — simple syntax;
    — PHP date() templates usage.



    Example 1 (syncronous datepicker):

    <code>
        <input id="date">

        <script type="text/javascript">
            var
                today  = new Date(),
                picker = new DatePicker(
                    {
                        select : function(data) {
                            console.log(data);
                        }
                    },
                    {
                        dom_field : document.getElementById('date')
                    }
                );

            picker.select(today);
        </script>
    </code>


    Example 2 (asyncronous datepicker):

    <code>
        <input id="date">

        <script type="text/javascript">
            var
                today  = new Date(),
                picker = new DatePicker(
                    {
                        select : function(data, fn) {
                            console.log(data);
                            fn.done();
                            fn.hide();
                        }
                    },
                    {
                        dom_field       : document.getElementById('date'),
                        async_selection : true
                    }
                );

            picker.select(today);
        </script>
    </code>


    Example 3 (without the input usage):

    <code>
        <script type="text/javascript">
            var
                today  = new Date(),
                picker = new DatePicker(
                    {
                        select : function(data) {
                            console.log(data);
                        }
                    },
                    {}
                );

            picker.select(today);
            picker.show();
        </script>
    </code>


    Example 4 (subscribe two datepickers to each other):

    <code>
        <input id="from"> — <input id="till">

        <script type="text/javascript">
            var
                today = new Date(),
                till  = new DatePicker(
                    {
                        select : function(data) {
                            console.log(data);
                        }
                    },
                    {
                        dom_field : document.getElementById('till'),
                    }
                ),
                from  = new DatePicker(
                    {
                        select : function(data) {
                            console.log(data);
                        }
                    },
                    {
                        dom_field : document.getElementById('from'),
                    }
                );

            DatePicker.sub('from', '<', 'till');
            DatePicker.sub('till', '>', 'from');

            from.select(today);
        </script>
    </code>



    Requirements:

    — JavaScript.



    Constructor params list:

     param | value
    ==========================================================================
     funcs | User defined handlers object.
    --------------------------------------------------------------------------
     conf  | DatePicker settings object.
    ==========================================================================


    Common settings list:

     param           | value
    ==========================================================================
     dom_id          | Id string which will be saved as
                     | b-datepicker_id_{{ dom_id }} className.
    --------------------------------------------------------------------------
     text_bwd        | InnerHTML for the left arrow.
    --------------------------------------------------------------------------
     text_fwd        | InnerHTML for the right arrow.
    --------------------------------------------------------------------------
     tmpl_hat        | Template for the calendar header.
    --------------------------------------------------------------------------
     dom_field       | DOM node for the field attached to the calendar
                     | instance. If not set, calendar can be showed only
                     | manually.
    --------------------------------------------------------------------------
     range_max       | Maximal date in the calendar range.
    --------------------------------------------------------------------------
     range_min       | Minimal date in the calendar range.
    --------------------------------------------------------------------------
     range_now       | Current date in the calendar range.
    --------------------------------------------------------------------------
     dom_target      | Node where the calendar HTML will be inserted
                     | (document.body by the default).
    --------------------------------------------------------------------------
     fill_field      | False if the attached field should not be filled
                     | with a selected date.
    --------------------------------------------------------------------------
     tmpl_field      | Template for the attached field value.
    --------------------------------------------------------------------------
     dictionaries    | Language settings. Should be given as an object with
                     | the following structure:
                     | {
                     |     'ru' : {...},
                     |     'ua' : {...},
                     |     'kz' : {...}
                     | }
                     |
                     | The full list of language settings see below.
    --------------------------------------------------------------------------
     auto_position   | False if you want to set the calendar position
                     | manually.
    --------------------------------------------------------------------------
     async_selection | True if you want to turn the calendar selection into
                     | asyncronous mode. It may be useful for any checks
                     | using AJAX before the date selection is done.
    ==========================================================================


    Language settings list:

    (each value can be an array or a string separated with
    the HumanDate.sep property)

     param    | value
    ==========================================================================
     ampm     | Localized ante meridiem and post meridiem date part.
              |
              | Contains the following keys:
              | — full  — full spelling (ante meridiem, post meridiem);
              | — lower — lowercased short spelling (am, pm);
              | — upper — uppercased short spelling (AM, PM).
    --------------------------------------------------------------------------
     common   | Common settings for the datepicker controls.
              |
              | Contains the following keys:
              | — bwd  — text for the bwd control title;
              | — fwd  — text for the fwd control title;
              | — hide — text for the hide control.
    --------------------------------------------------------------------------
     monthes  | Localized monthes names.
              |
              | Contains the following keys:
              | — decl — declensioned month names (of December, of November);
              | — full — full name month names (December, November);
              | — part — Three letter month names (Dec, Nov).
    --------------------------------------------------------------------------
     holidays | List of holidays in Y-m-d format.
    --------------------------------------------------------------------------
     weekdays | Localized weekdays names.
              |
              | Contains the following keys:
              | — motu — two letter weekday name (Mo, Tu);
              | — full — full weekday name (Monday, Tuesday);
              | — part — Three letter weekday name (Mon, Tue).
    ==========================================================================


    User defined handlers list:

     handler     | runs when
    ==========================================================================
     hide()      | The calendar is hiding.
    --------------------------------------------------------------------------
     seek()      | The calendar is switching between the monthes.
    --------------------------------------------------------------------------
     show()      | The calendar is showing.
    --------------------------------------------------------------------------
     select()    | Some date in the calendar is selected before the
                 | selection was made.
    --------------------------------------------------------------------------
     deselect () | The date selection in calendar is removing.
    ==========================================================================



    DatePicker instance properties:

     property    | description
    ==========================================================================
     id          | Calendar instance id as number or string.
    --------------------------------------------------------------------------
     shown       | Indicator of the calendar visibility.
    --------------------------------------------------------------------------
     subscribers | Calendars instances subscribed to this instance.
    ==========================================================================


    DatePicker instance methods:

     method      | description
    ==========================================================================
     bwd()       | Show the previous month.
    --------------------------------------------------------------------------
     fwd()       | Show the next month.
    --------------------------------------------------------------------------
     max()       | Set the maximal date in the calendar range.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     min()       | Set the minimal date in the calendar range.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     now()       | Set the current date in the calendar range.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     init()      | DatePicker initialization.
                 |
                 | Takes two arguments:
                 | — user defined handlers as object;
                 | — instance settings as object.
    --------------------------------------------------------------------------
     fill()      | Fill the attached field with the value.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     hide()      | Hide the calendar.
    --------------------------------------------------------------------------
     lang()      | Switch the language to default or any set in the
                 | instance settings object. Or set a new one.
                 |
                 | Takes two arguments:
                 | — two-letter language alias (en, ru, ua, etc...);
                 | — calendar elements translations as object (optional).
    --------------------------------------------------------------------------
     seek()      | Move calendar to a needed date.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     show()      | Show the calendar.
    --------------------------------------------------------------------------
     place()     | Set the DOM top and left styles manually or using
                 | the stylesheet.
                 |
                 | Takes one argument:
                 | — top and left position in pixels as object without
                 |   «px» in the end (optional).
    --------------------------------------------------------------------------
     reset()     | Remove all selections and return the calendar instance
                 | into default state.
    --------------------------------------------------------------------------
     select()    | Select a date in the calendar.
                 |
                 | Takes one argument:
                 | — date as number, string or Date object.
    --------------------------------------------------------------------------
     deselect()  | Remove the selection
    --------------------------------------------------------------------------
     uninstall() | Remove the calendar instance.
    ==========================================================================



    DatePicker static properties:

     property  | description
    ==========================================================================
     total     | Number of DatePicker instances.
    --------------------------------------------------------------------------
     installed | All DatePicker instances.
    ==========================================================================


    DatePicker static methods:

     method    | description
    ==========================================================================
     sub       | Subscribe one DatePicker instance to another.
               |
               | Takes three arguments.
               | — the child calendar id as number or string;
               | — relationship indicator (<, =, >);
               | — the parent calendar id as number or string.
    --------------------------------------------------------------------------
     hide      | Hide all calendars.
    --------------------------------------------------------------------------
     seek      | Move all calendars to a given date.
               |
               | Takes one argument:
               | — date as number, string or Date object.
    --------------------------------------------------------------------------
     show      | Show all calendars.
    --------------------------------------------------------------------------
     unsub     | Unsub one DatePicker instance from another.
               |
               | Takes two arguments:
               | — the child calendar id as number or string;
               | — the parent calendar id as number or string.
    --------------------------------------------------------------------------
     uninstall | Delete all calendar instances.
    ==========================================================================