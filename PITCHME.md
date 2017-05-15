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

<!-- .element: class="fragment" -->

```
foreach ($items as $item) {
	if( ! $item->published) {
		continue;
	}

	$this->doSomethingWithTheItem($item);
}
```

---

### #3 Do not use else

- No else after return
- Return early
- Defensive checks (check for negative => exceptions)
- Golden path (main code after the checks)
- Move checks to a separate method (only when making sense, when expecting multiple checks)
- Many elsifs on a single variable? => Switches

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
|
```
foreach ($items as $key => $value) {
	echo '<p>' . $key . ': ' . $value;
}
```
|
```
foreach ($items as $number => $name) {
	echo '<p>' . $number . ': ' . $name;
}
```
