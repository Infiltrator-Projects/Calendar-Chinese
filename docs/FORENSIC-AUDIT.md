# Traditional Chinese Lunisolar Calendar: forensic requalification, 27 October 2026

The previously reproduced ICU 74 date discrepancies are corrected in this provider's owned chronology. The original Common source remains unchanged.

- 73,049 daily reference-date checks passed against HKO Gregorian 1901–2100.
- 54,217 period/year/start navigation checks and 4,948 numeric day-format checks passed.
- 2,324 month-navigation checks across the 1900 and 2101 joins passed, with no tested date discontinuities.
- The updated UBSan/domain/failure-contract audit found no failures; UTF-8/length/capacity checks passed under 13 locale settings.
- `make check` includes the daily published-month fixture checker. `make audit-authorities` now passes all formerly failing recorded cases.

## Implementation and scope

Provider-owned Chinese lunisolar year data for 1900–2100, independently checked against the HKO 1901–2100 published tables; ICU supplies locale text and the retained projection outside that year table.

The table is packed from Unicode ICU4X year facts, whose source URLs and hashes are retained in `LUNAR-DATA-PROVENANCE.json`. Independent government/table data are stored as compact month references in `tests/published-months.json`; they do not come from provider output. Unicode license notices are retained in `licenses/Unicode-3.0.txt`.

Period navigation uses month ordinals, including intercalary months. Year navigation has an explicit policy: if a leap month is absent in the target year, use the following ordinary month. Day numbers clamp to the target month's length. Localized month/cycle/day text is composed from checked ICU text samples, retaining the real JDN weekday; it cannot replace the owned date with ICU's approximate date.

Finite tests establish the stated model and checked ranges. They do not certify every historical regional calendar, future official changes, every ICU/CLDR version or another operating system. Date-only JDN fields do not implement an intraday sunset rollover.

The HKO English text omits 2069-12-30. That single lunar day is uniquely inferred as 17 from 2069-12-29/day 16 and 2069-12-31/day 18. The report distinguishes 73,048 directly published rows from this one derived row.

When both endpoints lie outside the owned table, nonzero navigation retains the existing ICU projection. Zero-step navigation is always identity, including a distant Dangi case where the old projection accidentally moved by two months. This preserves projection compatibility without presenting it as historically verified.
