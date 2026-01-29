# Patch Notes

## v1.0.3 - Micro.blog Compatibility Fix

**Fixed:** Multiple issues preventing theme from working with micro.blog

**Issues:** 
1. Template trying to access `.Params.tags` on posts without tags
2. Using `"Type" "in" site.Params.mainSections` instead of micro.blog's `"Type" "posts"`
3. baseof.html not using micro.blog's partial system
4. Using `.Plain | truncate 30` for untitled posts instead of generic text

**Solutions:**
- Added `{{ if .Params.tags }}` checks before accessing tag arrays
- Changed all templates to use `where .Site.RegularPages "Type" "posts"` 
- Updated baseof.html to work with Bear's partial system while injecting custom CSS
- Used `.Plain | truncate 30` for consistency with Bear theme behavior
- Removed pagination logic since micro.blog handles that differently

**Files modified:**
- `layouts/index.html`
- `layouts/_default/home.html`  
- `layouts/_default/list.html`
- `layouts/_default/baseof.html`
- `layouts/tags/taxonomy.html`

**Note:** This version should work out of the box with micro.blog's post structure.

---

## v1.0.2 - Homepage Template Fix

**Fixed:** Homepage not showing new theme styling

**Issue:** 
The homepage (https://csv.micro.blog) was still showing the Bear theme while other pages showed the new CSV Changelog theme.

**Solution:**
Added multiple homepage template alternatives to ensure micro.blog picks up the correct one:
- `layouts/_default/home.html` - Specific homepage template (highest priority)
- `layouts/_default/list.html` - Generic list template for collections
- Updated `layouts/index.html` to use `.Paginator.Pages` for proper pagination

Hugo/micro.blog uses a template lookup order, and we needed to cover all the bases.

**Files added:**
- `layouts/_default/home.html`
- `layouts/_default/list.html`

**Files modified:**
- `layouts/index.html`

---

## v1.0.1 - Template Fix

**Fixed:** Type conversion error with `time.Weekday` in Hugo templates

**Issue:** 
```
error calling int: unable to cast 3 of type time.Weekday to int
```

**Solution:**
Removed the complex weekday calculation that tried to cast `time.Weekday` to int. Simplified the week number calculation to use `YearDay` directly:

```go
// Old (broken)
{{ $weekStart := .Date.AddDate 0 0 (int (sub 1 (int .Date.Weekday))) }}

// New (fixed)
{{ printf "%02d" (div .Date.YearDay 7 | add 1) }}
```

**Files modified:**
- `layouts/index.html`
- `layouts/tags/taxonomy.html`

**Note:** The week links still work, they just use a simpler calculation based on day of year rather than trying to calculate the start of the week. This is more compatible with Hugo's type system.

