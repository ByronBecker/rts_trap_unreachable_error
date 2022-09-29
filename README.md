# rts_trap_unreachable_error

## Motivation

```
for (i in Iter.range(0, 200000000000000)) {};
```

Running a very long for loop (see the above) results in the following error 
```
Error: failed to run main module `Test.wasm`

Caused by:
    0: failed to invoke command default
    1: wasm trap: wasm `unreachable` instruction executed
       wasm backtrace:
           0:  0x3b6 - <unknown>!rts_trap
           1: 0xcef0 - <unknown>!motoko_rts::trap_with_prefix::hbb665872bf969d20
           2: 0xb34d - <unknown>!motoko_rts::rts_trap_with::h91063078d15271f7
           3: 0xb5d3 - <unknown>!motoko_rts::memory::ic::grow_memory::hb99ecdf4fcf0660e
           4: 0xd226 - <unknown>!mp_calloc
           5:  0xf16 - <unknown>!mp_init
           6: 0xa09e - <unknown>!bigint_of_int64
           7:  0x5d2 - <unknown>!B_gt
           8:  0x6e2 - <unknown>!next
           9:  0x469 - <unknown>!init
          10:  0x73b - <unknown>!_start
```

## How to reproduce

1. Have vessel installed
2. Run `make run-example`