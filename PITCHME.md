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

```
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
- No else after return	|

---

```
function checkPublished($article) {

	if ( $article->published) {
		return 'Yes, it is published';
	} else {
		return 'No, not published';
	}

}
```
---

```
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

```
function checkPublished($article) {

	if ( $article->published) {
		return 'Yes, it is published';
	}

	return 'No, not published';

}
```
---

```
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

```
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

```
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

### #3 Do not use else
#### Switches

```
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

### #3 Do not use else
#### Switches

```
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

### #3 Do not use else
#### Switches

```
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
- Move checks to a separate method (only when making sense, when expecting multiple checks) |

---

### #4 Do not abbreviate

Exceptions:
- `id` for identifier


---

### #4 Do not abbreviate

```
foreach ($items as $i => $v) {
	echo '<p>' . $i . ': ' . $v;
}
```
<!-- .element: class="fragment" -->
```
foreach ($items as $key => $value) {
	echo '<p>' . $key . ': ' . $value;
}
```
<!-- .element: class="fragment" -->
```
foreach ($items as $number => $name) {
	echo '<p>' . $number . ': ' . $name;
}
```
<!-- .element: class="fragment" -->
