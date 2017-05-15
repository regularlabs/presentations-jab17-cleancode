<div class="logo">
![LOGO](assets/logo.png)
</div>

## Cleaning up your code
### The low hanging fruit

---

## Disclaimer

Thanks to
- Jeff Bay (Object Calisthenics 2008)
- Rafael Dohms (Object Calisthenics for PHP)
- Jeffrey Way (Laracasts)

---

## Goals

- Readability
- More stable	|
- Maintainabiliy	|
- Better testable	|
- DRYer	|

---

## Goals

- <span class="special">Re</span>adability
- <span class="special">M</span>ore stabl<span class="special">e</span>
- <span class="special">M</span>aintainabiliy
- <span class="special">Be</span>tter testable
- D<span class="special">R</span>Yer

---


Here is some code:

```
		if (empty($string) || empty($area))
		{
			return $string;
		}
```