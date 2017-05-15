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

- <span style="color:green">Re</span>adability
- <span style="color:blue">M</span>ore stabl<span style="color:green">e</span>
- <span style="color:red">M</span>aintainabiliy
- <span style="color:lightblue">Be</span>tter testable
- D<span style="color:green">R</span>Yer

---


Here is some code:

```
		if (empty($string) || empty($area))
		{
			return $string;
		}
```