---
title: Chapter
description: >-
  The first chapter


---
## New subexercises

```yaml
type: TabExercise
lang: sql
xp: 100
key: ecc1838fc7
```

This is what new tab exercises look like.



`@pre_exercise_code`
```{python}
connect('postgresql', 'films')
set_options(visible_tables = ['films'])
```
`@sample_code`
```{sql}
-- Nothing here
```




***



```yaml
type: NormalExercise
xp: 30
key: 44e6396db4
```



`@instructions`
Get the title and release year for films released in the 90s.

`@hint`
```
SELECT ___, ___
FROM ___
WHERE ___ >= 1990 AND ___ < 2000;
```



`@solution`
```{sql}
SELECT title, release_year
FROM films
WHERE release_year >= 1990 AND release_year < 2000;
```
`@sct`
```{python}
sel = check_node('SelectStmt')

title = test_column('title', msg='Did you select the `title` column?')

release_year = test_column('release_year', msg='Did you select the `release_year` column?')

from_clause = sel.check_field('from_clause')

where_clause = sel.check_field('where_clause')

where_release_year1 = where_clause.has_equal_ast(sql='release_year >= 1990', start='expression', exact=False, msg='Did you check the `release_year` correctly in your `WHERE` clause?')

where_release_year2 = where_clause.has_equal_ast(sql='release_year < 2000', start='expression', exact=False, msg='Did you check the `release_year` correctly in your `WHERE` clause?')

Ex().test_correct(check_result(), [
    from_clause,
    where_release_year1,
    where_release_year2,
    title,
    release_year,
    test_has_columns(),
    test_ncols(),
    test_error()
])
```




***



```yaml
type: NormalExercise
xp: 30
key: 46ebaa7fb3
```



`@instructions`
Now, build on your query to filter the records to only include French or Spanish language films.

`@hint`
```
SELECT ___, ___
FROM ___
WHERE (___ >= 1990 AND ___ < 2000)
AND (___ = 'French' OR ___ = 'Spanish');
```



`@solution`
```{sql}
SELECT title, release_year
FROM films
WHERE (release_year >= 1990 AND release_year < 2000)
AND (language = 'French' OR language = 'Spanish');
```
`@sct`
```{python}
sel = check_node('SelectStmt')

title = test_column('title', msg='Did you select the `title` column?')

release_year = test_column('release_year', msg='Did you select the `release_year` column?')

from_clause = sel.check_field('from_clause')

where_clause = sel.check_field('where_clause')

where_release_year1 = where_clause.has_equal_ast(sql='release_year >= 1990', start='expression', exact=False, msg='Did you check the `release_year` correctly in your `WHERE` clause?')

where_release_year2 = where_clause.has_equal_ast(sql='release_year < 2000', start='expression', exact=False, msg='Did you check the `release_year` correctly in your `WHERE` clause?')

where_language1 = where_clause.has_equal_ast(sql="language = 'French'", start='expression', exact=False, msg='Did you check the `language` correctly in your `WHERE` clause?')

where_language2 = where_clause.has_equal_ast(sql="language = 'Spanish'", start='expression', exact=False, msg='Did you check the `language` correctly in your `WHERE` clause?')


Ex().test_correct(check_result(), [
    from_clause,
    where_release_year1,
    where_release_year2,
    where_language1,
    where_language2,
    title,
    release_year,
    test_has_columns(),
    test_ncols(),
    test_error()
])
```




***



```yaml
type: NormalExercise
xp: 30
key: 268b574f8b
```



`@instructions`
Finally, restrict the query to only return films that took in more than $2M gross.

`@hint`
```
SELECT ___, ___
FROM ___
WHERE (___ >= 1990 AND ___ < 2000)
AND (___ = '___' OR ___ = '___')
AND ___ > ___;
```



`@solution`
```{sql}
SELECT title, release_year
FROM films
WHERE (release_year >= 1990 AND release_year < 2000)
AND (language = 'French' OR language = 'Spanish')
AND gross > 2000000;
```
`@sct`
```{python}
sel = check_node('SelectStmt')

title = test_column('title', msg='Did you select the `title` column?')

release_year = test_column('release_year', msg='Did you select the `release_year` column?')

from_clause = sel.check_field('from_clause')

where_clause = sel.check_field('where_clause')

where_release_year1 = where_clause.has_equal_ast(sql='release_year >= 1990', start='expression', exact=False, msg='Did you check the `release_year` correctly?')

where_release_year2 = where_clause.has_equal_ast(sql='release_year < 2000', start='expression', exact=False, msg='Did you check the `release_year` correctly in your `WHERE` clause?')

where_language1 = where_clause.has_equal_ast(sql="language = 'French'", start='expression', exact=False, msg='Did you check the `language` correctly in your `WHERE` clause?')

where_language2 = where_clause.has_equal_ast(sql="language = 'Spanish'", start='expression', exact=False, msg='Did you check the `language` correctly in your `WHERE` clause?')

where_gross = where_clause.has_equal_ast(sql='gross > 2000000', start='expression', exact=False, msg='Did you check the `gross` correctly in your `WHERE` clause?')

Ex().test_correct(check_result(), [
    from_clause,
    where_release_year1,
    where_release_year2,
    where_language1,
    where_language2,
    where_gross,
    title,
    release_year,
    test_has_columns(),
    test_ncols(),
    test_error()
])
```




---
## This is a normal exercise title

```yaml
type: NormalExercise
key: 639c3ece71
```



`@instructions`


`@hint`








