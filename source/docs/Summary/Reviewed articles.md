**Survey:**
```dataview
TABLE 
Link, 
Year, 
Datasets, 
Metrics,
length(file.inlinks) as Signif
FROM "docs/Publications/Articles"
WHERE Reviewer AND Type = "Survey"
```


**Research:**
```dataview
TABLE 
Link, 
Year, 
Direction, 
Code, 
Novelty, 
Overview, 
Datasets, 
Metrics,
length(file.inlinks) as Signif
FROM "docs/Publications/Articles"
WHERE Reviewer AND Type = "Research"
```
