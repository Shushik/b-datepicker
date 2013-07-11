
    b-datepicker — customized calendar/datepicker control.
    Working example: http://silkleo.ru/fun/b-datepicker/



    Goods:

    — no external libraries required (pure JavaScript);
    — simple syntax;
    — PHP date() templates usage.



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
                     | .b-datepicker_id_{{ dom_id }} className.
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
                     | by a selected date.
    --------------------------------------------------------------------------
     tmpl_field      | Template for the attached field value.
    --------------------------------------------------------------------------
     auto_position   | False if you want to set the calendar position
                     | manually.
    --------------------------------------------------------------------------
     async_selection | True if you want to turn the calendar selection into
                     | asyncronous mode. It may be useful for any checks
                     | using AJAX before the date selection is done.
    ==========================================================================


    User defined handlers list:

     handler   | runs when
    ==========================================================================
     .hide()   | The calendar is hiding.
    --------------------------------------------------------------------------
     .seek()   | The calendar is switching between the monthes.
    --------------------------------------------------------------------------
     .show()   | The calendar is showing.
    --------------------------------------------------------------------------
     .select() | Some date in the calendar is selected before the selection
               | was made.
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