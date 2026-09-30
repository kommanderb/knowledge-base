# ACID

Atomicity
	if a part of the transaction fails, all transaction fails
Consistency
	every transaction keeps the data valid, all constraints are satisfied
Isolation
	transaction occurs like they are played one after another
Durability
	after a transaction occured, data is resilient to restart and crash

# BASE

Basically Available
	The system keeps responding, even during failures or partition
Soft state
	Data may temporarily differ between replicas or changes in the background
Eventually consistent
	Over time (and with no new writes), all replicas converge to the same value
