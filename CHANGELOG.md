# PrettyTable 1.0.1 and newer

See GitHub Releases:

- https://github.com/prettytable/prettytable/releases

# PrettyTable 1.0 - October 4, 2020

- Dropped support for EOL Python 2.4-2.6 and 3.0-3.4.
- Added support for Python 3.5-3.9.
- Added `del_column(field_name)`.
- Added `get_csv_string` with `delimiter` option (comma or tab) and optional `header`.
- Use wcwidth for better wide char support.
- New `paginate` method can be used to produce strings suitable for piping to lp/lpr.
- `from_html` now handles HTML tables with colspan, rather than choking on them.
- Added `min_width`, `min_table_width` and `max_table_width` attribute/options for
  better control of table sizing.
- Added "title" attribute/option for table titles.
- When slice syntax is used to create a new sub-table out of an existing table, the rows
  are sorted before, not after, the slicing. The old behaviour (slice then sort) can be
  achieved by setting `oldsortslice=True`.
- The `from_csv` table factory now accepts CSV format parameters as keyword arguments
  (e.g. `delimiter`, `doublequote`, `escapechar`, etc.)
- Added 0x000f to the list of special characters with width 0, to fix problems with
  coloured strings produced by the Blessings library.
- Fixed constructor argument `float_format` to work as intended.
- Removed `print_html()` from README.
- Added `from_json` and `get_json_string` to PrettyTable.
- Fixed `PLAIN_COLUMN` to `PLAIN_COLUMNS` in README.
- Added Markdown and Org mode styles.

# PrettyTable 0.7 - Feb 17, 2013

- Improved Python 2 and 3 compatibility (2.4-3.2).
- Improved support for non-Latin characters. Table widths should now be calculated
  correctly for tables with e.g. Japanese text.
- Table contents can now be read in from a .csv file
- Table contents can now be read in from a DB-API compatible cursor
- Table contents can now be read in from a string containing an HTML table (thanks to
  Christoph Robbert for submitting this patch!)
- New `valign` attribute controls vertical alignment of text when some cells in a row
  have multiple lines of text and others don't. (thanks to Google Code user maartendb
  for submitting this patch!)
- `hrules` attribute can now be set to HEADER, which draws a rule only under the header
  row
- New `vrules` attribute controls drawing of vertical rules and can be set to `FRAME`,
  `ALL` or `NONE`
- New `header_style` attribute controls formatting of text in table headers and can be
  set to `cap`, `title`, `upper`, `lower` or `None`
- Fixed a simple bug regarding validation of `max_width` (thanks to Anthony Toole for
  pointing out this bug and providing a patch).
- Fixed a simple bug regarding initialisation of `int_format` value for new tables
  (thanks to Ingo Schmiegel for pointing out this bug!)
- Fixed a bug regarding some constructor keywords, such as `border`, being ignored
  (thanks to Google Code user antonio.s.messina for reporting this bug).

# PrettyTable 0.6 - May 5, 2012

- Code is now simultaneously compatible with Python 2 and 3
- Replaced all setter methods with managed attributes
- All styling options can now be set persistently as managed attributes
- Added `add_style` method to make setting style options easily
- Added `del_row`, `clear_rows` and `clear` methods to facilitate removal of data from
  table.
- Added `copy` method to facilitate cloning of a table.
- Removed caching functionality, which added complexity and fragility for relatively
  little gain
- Removed methods that just printed strings produced by `get_string` and
  `get_html_string` - just use inbuilt print!
- Improved unicode support (thanks to Google Code user ru.w31rd0 for patch!)
- Added support for decimal and floating point number formatting support (thanks to
  Google Code user willfurnass for the suggestion!)
- Added support for using a custom key sorting methods (thanks to Google Code user
  amannijhawan for the suggestion!)
- Added support for line breaks in data (suggested and implemented by Klein Stephane)
- Added support for max column widths (thanks to Tibor Arpas for the suggestion!)
- Fixed table slicing
- Fixed bug where closing `<tr/>` tags in HTML tables were not printed (thanks to Google
  Code user kehander for reporting this bug!)
- Fixed HTML table sorting bug (thanks to Google Code user dougbeal for reporting this
  bug!)
- Fixed bug whereby changing field_names did not recompute widths (thanks to Google Code
  user denilsonsa for reporting this bug!)

# PrettyTable 0.5 - May 26, 2009

- Fixed a bug whereby printing with `headers=False` and `border=False` would introduce
  an extraneous newline. Thanks to Alexander Lamaison for reporting this bug.
- When printing with `headers=False`, column widths will now be reduced as appropriate
  in columns where the field name is wider than the data. Thanks to Alexander Lamaison
  for suggesting this behaviour.
- Support for Unicode has improved. Thanks to Chris Clark for submitting this
  improvement.
- The value of the `border` argument now correctly controls the presence of a border
  when printing HTML tables with print_html or `get_html_string`, instead of being
  incorrectly ignored. Thanks to Chris Clark for fixing this.
- The `print_html` and `get_html_string` methods now accept an `attributes` argument
  which is a dictionary of name/value pairs to be placed inside the `<table>` tag (so
  you can, e.g. set `class`, `name` or `id` values in order to style your table with
  CSS). Thanks to Chris Clark for submitting this feature.
- The print_html and get_html_string methods now, by default, do their best to match the
  various formatting options in their HTML output. They use inline CSS to adjust the
  alignment of data in columns, the padding widths of columns and in some cases the
  border settings. You can give either method a `format=False` attribute to turn this
  behaviour off if you want to do your own styling. With `format=False` the methods
  print a "bare bones" table, similar to the default behaviour in 0.4.

# PrettyTable 0.4 - May 13, 2009

- Added `add_column` method to enable building tables up column-by-column.
- Added `print_HTML` and `get_HTML_string` methods to enable HTML table production.
- Added `set_border_chars` method to enable control over characters used to draw the
  table border.
- Added `set_left_padding` and `set_right_padding` methods to allow independent padding
  control for both sides of a column.
- Added `sortby` option to enable column sorting.
- Added `header` option to enable switching off field name printing at top of table.
- Modified `hrules` option to enable greater control over presence of horizontal lines.
- Added `border` option to enable switching off all line printing.

Thanks to Tim Cera, Chris Clark, Alexander Lamaison for suggesting and helping to test
many of the new features in this release.

# PrettyTable 0.3 - May 01, 2009

- Added `padding_width` option to control the number of spaces between the vertical line
  rules at the edges of a column and its content. This can be set as a keyword argument
  to the constructor or after instantiation using the `set_padding_width` method. The
  value is set to `1` by default. If your table is too wide for a small screen with this
  value, setting it to `0` might help you squeeze it in.

Thanks to Chris Clark for contributing a patch against 0.2.1 to add this feature!

# PrettyTable 0.2.1 - April 29, 2009

- Caching no longer breaks when using the `printt(fields=[...])` syntax. The list of
  fields was not hashable and hence could not be used as a dictionary key. I fixed this
  using the output of the `cPickle` module's `dumps` function as the dictionary key
  instead.
- Horizontal lines are now the appropriate length when the above syntax is used.

Thanks to Julien Koesten for reporting these bugs and testing the fixes almost
immediately after the release of 0.2!

# PrettyTable 0.2 - April 29, 2009

- Added `get_string` method.
- Added `__str__` method (which just calls `get_string`) to enable nice `print x`
  syntax.
- Can now pass field names as a constructor argument.
- Return values of `get_string` are cached in a dictionary that is only cleared after a
  call to `add_row` or something else which invalidates the cache.

# PrettyTable 0.1 - February 26, 2009

- Original release
