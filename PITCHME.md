<div class="logo">
![LOGO](assets/logo.png)
</div>

## Cleaning up your code
### The low hanging fruit

---

## Thanks to

- Jeff Bay (Object Calisthenics 2008)
- Rafael Dohms (Object Calisthenics for PHP)
- Jeffrey Way (Laracasts)

---


## Refactoring

Small steps to better code

---


## Goals

- Readability
- More stable		|
- Maintainabiliy	|
- Better testable	|
- DRYer				|

---


## Goals

- <span class="special">Re</span>adability
- <span class="special">M</span>ore stabl<span class="special">e</span>
- <span class="special">M</span>aintainabiliy
- <span class="special">Be</span>tter testable
- D<span class="special">R</span>Yer

---


### #1 Keep your classes (and methods) small

---


### #2 One level of indentation

```php
function doSomethingWithTheItemList($items) {

	foreach ($items as $item) {
		if( ! $item->published) {
			continue;
		}

		$this->doSomethingWithTheItem($item);
	}

}
```
<!-- .element: class="fragment" -->

---


### #3 Do not use else

- Golden path	|

---

<div class="mono">
.
/ \
.  .
/ \  / \
.  .  .  .
/ \ / \ / \ / \
.  .  .  .  .  .  .  .
</div>

---


### #3 Do not use else

- Golden path
- No else after return	|

---

```php
function checkPublished($article) {

	if ( $article->published) {
		return 'Yes, it is published';
	} else {
		return 'No, not published';
	}

}
```

---

```php
function checkPublished($article) {

	if ( $article->published) {
		return 'Yes, it is published';
	}

	return 'No, not published';

}
```
---

### #3 Do not use else

- Golden path
- No else after return
- Defensive (negative) checks |

---

```php
function checkPublished($article) {

	if ( $article->published) {
		return 'Yes, it is published';
	}

	return 'No, not published';

}
```
---

```php
function checkPublished($article) {

	if ( ! $article->published) {
		return 'No, not published';
	}

	return 'Yes, it is published';

}
```
---

### #3 Do not use else

- Golden path
- No else after return
- Defensive (negative) checks
- Return early |

---

```php
function checkAges($age1, $age2) {

	if ($age1 < $age2) {
		$result = 'younger';
	} else if ($age1 > $age2) {
		$result = 'older';
	}  else {
		$result = 'same';
	}

	return $result;

}
```
---

```php
function checkAges($age1, $age2) {

	if ($age1 < $age2) {
		return 'younger';
	}

	if ($age1 > $age2) {
		return 'older';
	}

	return 'same';

}
```

---
### #3 Do not use else

- Golden path
- No else after return
- Defensive (negative) checks
- Return early
- Many else-ifs => Switches |

---

```php
function getStatusText($status) {

	if ($status == -2) {
		$result = 'Archived';
	} else if ($status == -1) {
		$result = 'Trashed';
	} else if ($status == 0) {
		$result = 'Unpublished';
	} esle {
		$result = 'Published';
	}

	return $result;

}
```
---

```php
function getStatusText($status) {

	if ($status == -2) {
		return 'Archived';
	}

	if ($status == -1) {
		return 'Trashed';
	}

	if ($status == 0) {
		return 'Unpublished';
	}

	return 'Published';

}
```

---

```php
function getStatusText($status) {

	switch ($status) {

		case -2:
			return 'Archived';

		case -1:
			return 'Trashed';

		case 0:
			return 'Unpublished';

		case 1:
		default:
			return 'Published';

	}

}
```

---

### #3 Do not use else

- Golden path
- No else after return
- Defensive (negative) checks
- Return early
- Many else-ifs => Switches
- Move checks to a separate method |

---


### #4 Do not abbreviate

- `val` => `value` |
- `` => `value` |

Exceptions: |
- `id` for identifier |
- `x` `y` for actual axis |

---

### #4 Do not abbreviate

```php
foreach ($items as $i => $v) {
	echo '<p>' . $i . ': ' . $v;
}
```
<!-- .element: class="fragment" -->
```php
foreach ($items as $key => $value) {
	echo '<p>' . $key . ': ' . $value;
}
```
<!-- .element: class="fragment" -->
```php
foreach ($items as $number => $name) {
	echo '<p>' . $number . ': ' . $name;
}
```
<!-- .element: class="fragment" -->
