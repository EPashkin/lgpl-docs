<!-- file value.rs -->
<!-- file_comment -->
Generic values — A polymorphic type that can hold values of any other type
<!-- impl Value::fn init -->
Initializes value with the default value of type .
<!-- impl Value::fn reset -->
Clears the current value in value and resets it to the default value (as if the
value had just been initialized).
<!-- impl Value::fn strdup_value_contents -->
Return a newly allocated string, which describes the contents of a GValue. The main
purpose of this function is to describe GValue contents for debugging output, the way
in which the contents are described may change between different GLib versions.
<!-- impl Value::fn compatible -->
Returns whether a GValue of type src_type can be copied into a GValue of type dest_type .
<!-- impl Value::fn transformable -->
Check whether g_value_transform() is able to transform values of type src_type into
values of type dest_type . Note that for the types to be transformable, they must be
compatible and a transform function must be registered.
<!-- file lib.rs -->
<!-- file_comment -->
Bindings and wrappers for __GLib__
<!-- file date.rs -->
<!-- file_comment -->
Date and Time Functions — calendrical calculations and miscellaneous time stuff
<!-- impl Date::fn new -->
Allocates a GDate and initializes it to a sane state. The new date will be cleared
(as if you'd called g_date_clear()) but invalid (it won't represent an existing day).
<!-- impl Date::fn new_dmy -->
Like g_date_new(), but also sets the value of the date. Assuming the day-month-year
triplet you pass in represents an existing day, the returned date will be valid.
<!-- impl Date::fn new_julian -->
Like g_date_new(), but also sets the value of the date. Assuming the Julian day
number you pass in is valid (greater than 0, less than an unreasonably large
number), the returned date will be valid.
<!-- impl Date::fn clear -->
Initializes one or more GDate structs to a sane but invalid state. The cleared
dates will not represent an existing date, but will not contain garbage. Useful
to init a date declared on the stack. Validity can be tested with g_date_valid().
<!-- impl Date::fn set_day -->
Sets the day of the month for a GDate. If the resulting day-month-year triplet is
invalid, the date will be invalid.
<!-- impl Date::fn set_month -->
Sets the month of the year for a GDate. If the resulting day-month-year triplet is
invalid, the date will be invalid.
<!-- impl Date::fn set_year -->
Sets the year for a GDate. If the resulting day-month-year triplet is invalid, the
date will be invalid.
<!-- impl Date::fn set_dmy -->
Sets the value of a GDate from a day, month, and year. The day-month-year triplet
must be valid; if you aren't sure it is, call g_date_valid_dmy() to check before
you set it.
<!-- impl Date::fn set_julian -->
Sets the value of a GDate from a Julian day number.
<!-- impl Date::fn set_time_t -->
Sets the value of a date to the date corresponding to a time specified as a time_t.
The time to date conversion is done using the user's current timezone.
To set the value of a date to the current day, you could write:
```
Date::new().set_time_t(date, time::get_time().sec);
```
<!-- impl Date::fn set_time_val -->
Sets the value of a date from a GTimeVal value. Note that the tv_usec member is ignored,
because GDate can't make use of the additional precision.

The time to date conversion is done using the user's current timezone.
<!-- impl Date::fn set_parse -->
Parses a user-inputted string str , and try to figure out what date it represents,
taking the current locale into account. If the string is successfully parsed, the
date will be valid after the call. Otherwise, it will be invalid. You should check
using g_date_valid() to see whether the parsing succeeded.

This function is not appropriate for file formats and the like; it isn't very precise,
and its exact behavior varies with the locale. It's intended to be a heuristic routine
that guesses what the user means by a given string (and it does work pretty well in
that capacity).
<!-- impl Date::fn add_days -->
Increments a date some number of days. To move forward by weeks, add weeks*7 days. The
date must be valid.
<!-- impl Date::fn subtract_days -->
Moves a date some number of days into the past. To move by weeks, just move by weeks*7
days. The date must be valid.
<!-- impl Date::fn add_months -->
Increments a date by some number of months. If the day of the month is greater than 28,
this routine may change the day of the month (because the destination month may not have
the current day in it). The date must be valid.
<!-- impl Date::fn subtract_months -->
Moves a date some number of months into the past. If the current day of the month doesn't
exist in the destination month, the day of the month may change. The date must be valid.
<!-- impl Date::fn add_years -->
Increments a date by some number of years. If the date is February 29, and the destination
year is not a leap year, the date will be changed to February 28. The date must be valid.
<!-- impl Date::fn subtract_years -->
Moves a date some number of years into the past. If the current day doesn't exist in the
destination year (i.e. it's February 29 and you move to a non-leap-year) then the day is
changed to February 29. The date must be valid.
<!-- impl Date::fn days_between -->
Computes the number of days between two dates. If date2 is prior to date1 , the returned
value is negative. Both dates must be valid.
<!-- impl Date::fn compare -->
qsort()-style comparison function for dates. Both dates must be valid.

returned value :
* 0 for equal
* < 0 if lhs is less than rhs
* > 0 if lhs is greater than rhs
<!-- impl Date::fn clamp -->
If date is prior to min_date , sets date equal to min_date . If date falls after
max_date , sets date equal to max_date . Otherwise, date is unchanged. Either of min_date
and max_date may be NULL. All non-NULL dates must be valid.
<!-- impl Date::fn order -->
Checks if date1 is less than or equal to date2 , and swap the values if this is not
the case.
<!-- impl Date::fn get_day -->
Returns the day of the month. The date must be valid.
<!-- impl Date::fn get_month -->
Returns the month of the year. The date must be valid.
<!-- impl Date::fn get_year -->
Returns the year of a GDate. The date must be valid.
<!-- impl Date::fn get_julian -->
Returns the Julian day or "serial number" of the GDate. The Julian day is simply the
number of days since January 1, Year 1; i.e., January 1, Year 1 is Julian day 1;
January 2, Year 1 is Julian day 2, etc. The date must be valid.
<!-- impl Date::fn get_weekday -->
Returns the day of the week for a GDate. The date must be valid.
<!-- impl Date::fn get_day_of_year -->
Returns the day of the year, where Jan 1 is the first day of the year. The date
must be valid.
<!-- impl Date::fn is_first_of_month -->
Returns true if the date is on the first of a month. The date must be valid.
<!-- impl Date::fn is_last_of_month -->
Returns true if the date is the last day of the month. The date must be valid.
<!-- impl Date::fn get_monday_week_of_year -->
Returns the week of the year, where weeks are understood to start on Monday. If
the date is before the first Monday of the year, return ???

The date must be valid.
<!-- impl Date::fn get_sunday_week_of_year -->
Returns the week of the year during which this date falls, if weeks are understood
to being on Sunday. The date must be valid. Can return 0 if the day is before the
first Sunday of the year.
<!-- impl Date::fn get_iso8601_week_of_year -->
Returns the week of the year, where weeks are interpreted according to ISO 8601.
<!-- impl Date::fn strftime -->
Generates a printed representation of the date, in a locale-specific way. Works
just like the platform's C library strftime() function, but only accepts date-related
formats; time-related formats give undefined results. Date must be valid. Unlike
strftime() (which uses the locale encoding), works on a UTF-8 format string and
stores a UTF-8 result.

This function does not provide any conversion specifiers in addition to those
implemented by the platform's C library. For example, don't expect that using
g_date_strftime() would make the %F provided by the C99 strftime() work on Windows
where the C library only complies to C89.
<!-- impl Date::fn is_valid -->
Returns TRUE if the GDate represents an existing day. The date must not contain
garbage; it should have been initialized with g_date_clear() if it wasn't allocated
by one of the g_date_new() variants.
<!-- struct TimeVal::variant tv_sec -->
seconds
<!-- struct TimeVal::variant tv_usec -->
microseconds
<!-- impl TimeVal::fn add -->
Adds the given number of microseconds to self . microseconds can also be negative to
decrease the value of self .
<!-- impl TimeVal::fn from_iso8601 -->
Converts a string containing an ISO 8601 encoded date and time to a GTimeVal and puts
it into self .

iso_date must include year, month, day, hours, minutes, and seconds. It can optionally
include fractions of a second and a time zone indicator. (In the absence of any time
zone indication, the timestamp is assumed to be in local time.)
<!-- impl TimeVal::fn to_iso8601 -->
Converts time_ into an RFC 3339 encoded string, relative to the Coordinated Universal
Time (UTC). This is one of the many formats allowed by ISO 8601.

ISO 8601 allows a large number of date/time formats, with or without punctuation and
optional elements. The format returned by this function is a complete date and time,
with optional punctuation included, the UTC time zone represented as "Z", and the tv_usec
part included if and only if it is nonzero, i.e. either "YYYY-MM-DDTHH:MM:SSZ" or
"YYYY-MM-DDTHH:MM:SS.fffffZ".

This corresponds to the Internet date/time format defined by RFC 3339, and to either of
the two most-precise formats defined by the W3C Note Date and Time Formats. Both of these
documents are profiles of ISO 8601.

Use g_date_time_format() or g_strdup_printf() if a different variation of ISO 8601 format
is required.
<!-- file source.rs -->
<!-- file_comment -->
Manages available sources of events for the main loop
<!-- file error.rs -->
<!-- impl Error::fn new_literal -->
Creates a new Error; unlike Error::new(), message is not a printf()-style format string.
Use this function if message contains text you don't have control over, that could include
printf() escape sequences.
<!-- impl Error::fn release -->
Frees an Error struct and associated resources.
<!-- impl Error::fn matches -->
Returns true if error matches domain and code , false otherwise. In particular, when error.pointer
is NULL, false will be returned.

If domain contains a FAILED (or otherwise generic) error code, you should generally not check
for it explicitly, but should instead treat any not-explicitly-recognized error code as being
equivalent to the FAILED code. This way, if the domain is extended in the future to provide a
more specific error code for a certain case, your code will still work.
<!-- impl Error::fn set -->
Does nothing if self.pointer is NULL; if self.pointer is non-NULL, then *self.pointer must be NULL.
A new GError is created and assigned to *self.pointer .
<!-- impl Error::fn propagate -->
If other.pointer is NULL, free self ; otherwise, moves self into other. The error variable
other.pointer points to must be NULL.

Note that self is no longer valid after this call. If you want to keep using the same Error
struct, you need to set it to NULL after calling this function on it.
<!-- impl Error::fn message -->
Returns the error message stored in the wrapped GError
<!-- file permission.rs -->
<!-- file_comment -->
GPermission — An object representing the permission to perform a certain action
<!-- impl Permission::fn get_allowed -->
Gets the value of the 'allowed' property. This property is true if the caller
currently has permission to perform the action that permission represents the
permission to perform.
<!-- impl Permission::fn get_can_acquire -->
Gets the value of the 'can-acquire' property. This property is true if it is
generally possible to acquire the permission by calling g_permission_acquire().
<!-- impl Permission::fn get_can_release -->
Gets the value of the 'can-release' property. This property is true if it is
generally possible to release the permission by calling g_permission_release().
<!-- impl Permission::fn impl_update -->
This function is called by the GPermission implementation to update the properties
of the permission. You should never call this function except from a GPermission
implementation.

GObject notify signals are generated, as appropriate.
