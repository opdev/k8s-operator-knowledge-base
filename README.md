# Certification process

Question:&#x20;

what part of the certification process requires `relatedImages` to be present in the `CSV` even when an operator does not have other images that it relies on (other than its own container image? As far as I know `preflight` doesn’t check for this nor does `operator-sdk validate bundle`

Answer:&#x20;

The Pipeline checks for it. It's a hard requirement for marketplace.
