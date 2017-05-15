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

- *Re*adability
- *M*ore stabl*e*
- *M*aintainabiliy
- *Be*tter testable
- D*R*Yer

---


Here is some code:

```
		if (empty($string) || empty($area))
		{
			return $string;
		}
```