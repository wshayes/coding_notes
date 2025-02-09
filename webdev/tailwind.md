## Tailwind Tips

- https://design2tailwind.com/blog/tailwindcss-background-image/
- Automatic concentric border radii with Tailwind - https://twitter.com/adamwathan/status/1710978528684957697
- `[&_svg]:open:-rotate-180` — Arbitrary Variant when clicking HTML element that can ‘open’ - this will rotate all child svg elements 180 degrees ([tip source](https://www.stefanjudis.com/today-i-learned/how-to-style-element-descendants-with-tailwind-css/?utm_campaign=tailwind-weekly-137&utm_source=Tailwind+Weekly))

```python
<div>
  <label for="location" class="block text-sm font-medium leading-6 text-gray-900">Location</label>
  <select id="location" name="location" class="mt-2 block w-full rounded-md border-0 py-1.5 pl-3 pr-10 text-gray-900 ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-indigo-600 sm:text-sm sm:leading-6">
  <option class="pl-0" value="1">Research</option>
  <option class="pl-4" value="2">Pharmacology</option>
  <option class="pl-0" value="3">Development</option>
  <option class="pl-4" value="4">BioStats</option>
  <option class="pl-8" value="5">Clin Data Mgmt</option>
  </select>
</div>
```

## Tailwind Example Code

- https://changelog.cursor.sh/?utm_campaign=tailwind-weekly-139&utm_source=Tailwind+Weekly - Changelog in the wild from TailwindUI