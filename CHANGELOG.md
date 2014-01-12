# Singularity Changelog

## v1.2.0

* **New** Sass 3.3.0 and Compass 1.0.0 compatibility
	* Sass 3.3.0 minimum required version
	* Compass no longer required to run (no custom Ruby dependencies)
* **New** Installable through Bower
* **New** [Breakpoint](http://github.com/team-sass/breakpoint) variables can now be used in `add-*`
* **New** Items added in `add-*` no longer need to be in order! They'll be sorted for you!
* **New** **Change** `grid-span` now takes an optional parameter `$gutter-style` (after `$output-style`, before `$options`) to allow you to specify gutter style/
* **New** `grid-span` options now can include a `from` key (left, right, or opposite) to specify the direction that should be used. If specifying a `from` direction, the `[dir="rtl"]` will not be printed. If your global direction is `rtl` or `both`, the selector will still be printed.
* **New** `isolation-span` and `float-span` both now have `$gutter-style` and `$from` parameters to pass them (respectively) to `grid-span`
* **New** **Change** When writing both `ltr` and `rtl` styles at the same time, styles whose properties are identical between `ltr` and `rtl` will not print out in the `rtl` style.
* **New** **DEPRECATION** Global variables for settings have been deprecated due to global namespacing issues that had to be changed. Instead, use `@include sgs-change($setting, $value)` to change a setting. Any setting that previously had dashes in their variable name (`$include-border-box` for instance) becomes a string of the variable name with spaces instead of dashes. Use `@include sgs-reset($setting)` to reset a setting.
* **DEPRECATION** `add-*` functions changed to `add-*` mixins to resolve global namespacing issues that had to be changed. Example: update `$grids: 12` to `@include add-grid(12)` and `$gutters: add-gutter(.5 at 500px)` to `@include add-gutter(.5 at 500px)`
* **DEPRECATION** push/pull/isolation mixins have been deprecated as they were always undocumented and untested and there doesn't appear to be many users using them as it was really only useful for `float`. Most users have migrated to `isolation` if push/pull/isolation was needed