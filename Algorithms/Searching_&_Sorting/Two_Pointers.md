[⬅ Back to Main Page](../../README.md)
# Reverse Postions in a list
```python
def reverse_specific_characters(s: str) -> str:
	word = list(s)
	start = 0
	end = len(word) - 1
	target_characters = "aeiouAEIOU"
	targets = set(list(target_characters))

	while start < end:
		while start < end and word[start] not in targets:
			start += 1
		while start < end and word[end] not in targets:
			end -= 1
		word[start], word[end] = word[end], word[start]
		start += 1
		end -= 1

	return "".join(word)
```
