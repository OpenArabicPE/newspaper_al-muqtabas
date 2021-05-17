- this repository only contains bibliographic metadata for issues I could track down, namely in the al-Aqṣā collection. This means there are substantial **gaps**.

# to do

- I think, I will need to regenerate all metadata from scratch because issue numbers do not match combinations of publication dates and EAP IDs
    - I originally generated TSS XML with **faulty issue numbers**: due to a lack of knowledge, I had not computationally accounted for weekdays on which al-Muqtabas hadn't been published.
        + result: issue numbers in the metadata tend to be larger than they should
        + not all of them had been fixed in Sente.
    - Problem upon import of automatically generated Zotero RDF into Zotero
        + `@rdf:about` is based on the BibTeX key,
        + BibTeX keys, in turn, are based on a combination of volume and issue numbers, which means that there will be duplicate keys
        + only the first reference will be imported into Zotero, subsequent "duplicates" (based on `@rdf:about`) are dropped
    - solution:
        + sort `<biblStruct>` by date
        + check the difference between the current node and the preceding node in Julian days
        + check if the difference in issue numbers is larger than the difference in Julian days. Account for weekdays, *al-Muqtabas* was certainly not published on

   ```{.xpath}
   //tei:monogr/tei:biblScope[@unit = 'issue'][1]/@from[. &lt;= preceding::tei:biblStruct[1]/tei:monogr/tei:biblScope[@unit = 'issue'][1]/@from]
   ```

- some volume numbers are missing

# OCLC IDs and publication history

+ *al-Muqtabas*
    * 1908-12-17 - 1909-
    * 1910-03-09 - 1913-09-24
    * 1914-02-01
    + oclc:70845599: Chicago Microfilm Project
    + oclc:1034546909: EAP with faulty publication dates (1906--1914)
+ *al-Qabas*: 1913-09-30 until 1914-01-29
    + oclc:792756309: al-Qabas
        + Muḥammad Kurd ʿAlī
        + Shukrī al-ʿAsalī
    + oclc:1034542938: al-Qabas
- *al-Umma*: early 1910 until 1910-03-08
    + oclc:1034544057
        + Aḥmad Kurd ʿAlī

## responsibilities

- No. 1 - 350

```xml
<tei:respStmt>
    <tei:resp>منشيء المقتبس ومدير سياستها</tei:resp>
    <tei:persName ref="oape:pers:878 viaf:32272677" xml:lang="ar">
        <tei:forename xml:lang="ar">محمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
```
- No. 353, 1910-04-26 - 1300, 1913-09-24

```xml
<tei:respStmt>
    <tei:resp>صاحب المقتبس ورئيس تحريره</tei:resp>
    <tei:persName ref="oape:pers:878 viaf:32272677" xml:lang="ar">
        <tei:forename xml:lang="ar">محمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
<tei:respStmt>
    <tei:resp>المدير المسؤول</tei:resp>
    <tei:persName xml:lang="ar">
        <tei:forename xml:lang="ar">احمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
```


- No. 429, 1910-07-23: new masthead design, but same information

```xml
<tei:respStmt>
    <tei:resp>صاحب المقتبس ورئيس تحريره</tei:resp>
    <tei:persName ref="oape:pers:878 viaf:32272677" xml:lang="ar">
        <tei:forename xml:lang="ar">محمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
<tei:respStmt>
    <tei:resp>المدير المسؤول</tei:resp>
    <tei:persName xml:lang="ar">
        <tei:forename xml:lang="ar">احمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
```

- No. 1301, 1913-09-30: *al-Qabas* until No.1400

```xml
<tei:respStmt>
    <tei:resp>صاحب الجريدة ومديرها المسؤول</tei:resp>
    <tei:persName xml:lang="ar">
        <tei:forename xml:lang="ar">شكري</tei:forename>
        <tei:surname xml:lang="ar">العسلي</tei:surname>
    </tei:persName>
</tei:respStmt>
<tei:respStmt>
    <tei:resp>رئيس التحرير</tei:resp>
    <tei:persName ref="oape:pers:878 viaf:32272677" xml:lang="ar">
        <tei:forename xml:lang="ar">محمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
```

- No. 1401, return to

```xml
<tei:respStmt>
    <tei:resp>صاحب المقتبس ورئيس تحريره</tei:resp>
    <tei:persName ref="oape:pers:878 viaf:32272677" xml:lang="ar">
        <tei:forename xml:lang="ar">محمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
<tei:respStmt>
    <tei:resp>المدير المسؤول</tei:resp>
    <tei:persName xml:lang="ar">
        <tei:forename xml:lang="ar">احمد</tei:forename>
        <tei:surname xml:lang="ar">كرد علي</tei:surname>
    </tei:persName>
</tei:respStmt>
```