# Queue-it Proof-of-Work

A Python solution for Queue-it's Proof-of-Work challenge (<https://queue-it.com/blog/proof-of-work-block-bad-bots/>).

## Usage

Usage:
```python
import base64, hashlib, json

def solveChallenge(input, zeroCount):
    zeros = "0" * zeroCount
    postfix = 0
    while True:
        postfix  += 1
        stri = input + str(postfix)
        encodedHash = hashlib.sha256(stri.encode()).hexdigest()
        if encodedHash.startswith(zeros):
            x = 10 * [{ "hash": encodedHash,"postfix": postfix }]
            return base64.b64encode(json.dumps(x, separators=(',', ':')).encode()).decode()
            
# GET THESE VALUES FROM THE RESPONSE WHEN FETCHING
# THE CHALLENGE AT .../challengeapi/pow/challenge/...
input = "f02b931c-52f0-4507-9406-f1221678dc16"
zeroCount = 2
# RETURNS THE CHALLENGE SOLUTION
solution = solveChallenge(input, zeroCount)
print(solution)
```

## Questions
For any questions feel free to add and DM me on Discord (eta#0001).

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change. Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)