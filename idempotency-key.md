# Idempotency Key

Encountered here: https://datatracker.ietf.org/doc/draft-ietf-httpapi-idempotency-key-header/

> Apply only on POST and PATCH

> Security consideration
	Short TTL (hours or days) -> should be documented
	Hash requests to compare Key+Hash to adapt response
		if response content is re-issued, it protects from brute forcing
		if not, 422 Unprocessable Content
		Consider using request Digest/Signature directly
	Middleware should execute after Throttle and Authorization

> Feature flag to force Idempotency
	Give time to adapt implementation if a client wants to activate max protection

> On server side
	Retry vs. Concurrent request
		Retry should re-issue last response
		Concurrent should answer 409 Conflict

Domain rules
	- There should be only one Idempotency-Key header (2.2)
	- [NTH] If key reused with different payload -> 422 Unprocessable content (2.2, 2.7)
	- [NTH] Use fingerprint derived from the key (2.4)
	- If key (and fingerprint if applicated) has not been seen, process the request without modification (2.6)
	- If key (AND fingerprint, if applicated) has been seen:
		-> if initial processing is over:
			[NTH] Return the initial result (2.6)
			Return a Conflict error (custom)
		-> if initial processing is not over, return a Conflict error (2.6, 2.7)

General rules
	- Keys TTL must be documented (2.3, 2.5)
