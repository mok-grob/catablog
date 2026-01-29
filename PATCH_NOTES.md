# Patch Notes

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

If you've already pulled the theme, update these two files in your repository.

