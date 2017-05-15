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

- <span class="color:green">Re</span>adability
- <span class="color:blue">M</span>ore stabl<span class="color:green">e</span>
- <span class="color:red">M</span>aintainabiliy
- <span class="color:green">Be</span>tter testable
- D<span class="color:green">R</span>Yer

---


Here is some code:

```
		if (empty($string) || empty($area))
		{
			return $string;
		}
```