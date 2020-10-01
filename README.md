Copyright © 2020 Digital Asset (Switzerland) GmbH and/or its affiliates
Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted.
THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL 
DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

# Trigger a time model error

- `daml build`
- `daml ledger upload-dar .daml/dist/the-horribly-slow-fibonacci-with-the-extremely-inefficient-algorithm-0.0.1.dar --host "$HOST" --port "$PORT"`
- `daml script --dar .daml/dist/the-horribly-slow-fibonacci-with-the-extremely-inefficient-algorithm-0.0.1.dar --script-name Test:run --ledger-host "$HOST" --ledger-port "$PORT" --input-file <(echo "$N")`
- increase "$N" until a time model error is reported, e.g. `Error: User abort: Submit failed with code 10: Invalid ledger time: Record time 2020-09-04T14:08:04.716Z outside of range [2020-09-04T14:06:55.408Z, 2020-09-04T14:07:55.408Z]`
- failures usually happen somewhere in the early 30s, a suggested progression can be `1 10 20 30 31 32 33...`

