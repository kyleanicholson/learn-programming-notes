2501231831

Status: #idea

Tags: 

# University Library

- Stack Used:
	- NextJs
- Dev dependencies
	- Prettier `npm i --save-dev prettier`
		- Manually enable this in settings after installation (node package)
		- Enable reformat on save
		- Enable Run on Save (applies eslint as well)
	- ESLint  (automatically installed)
		- Manual configuration - point to the package + find the directory 
		- Enable run ESlint -- fix on save
		- In file eslint.config.mjs: `..compat.extends("next/core-web-vitals","next/typescript", "standard", "plugin:tailwindcss/recommended", "prettier"),`
- Fonts
	- A folder containing fonts can be pasted directly into the app folder
---
# References
https://www.youtube.com/watch?v=EZajJGOMWas