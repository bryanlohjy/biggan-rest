# BigGAN Rest API

Adapted from Joel Simon's [Ganbreeder](https://github.com/joel-simon/ganbreeder) project.

## Installation

### Prerequisites
* Python 3 + pip

### Launch the BigGAN server
```bash
# Install dependencies
pip install -r requirements.txt
# And go...
python server.py
```
Your BigGAN server will be available at http://localhost:5000/

## Endpoints
### Random
#### Example Request
```javascript
fetch('http://localhost:5000/random', {
  method: 'POST',
  headers: {
    'Accept': 'application/json',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  body: 'num=5' // number of randoms to generate
});
```

#### Response
```javascript
[
  {
    vector: [], // 128D latent z vector
    label: [],  // 1000D label vector corresponding to the BigGAN Labels
    img: ''     // base64 string
  },
  ...
]
```

### Decode
Decode a latent vector into an image.
#### Example Request
```javascript
const vec = [];   // 128D latent z vector
const label = []; // 1000D label vector corresponding to the BigGAN Labels

fetch('http://localhost:5000/decode', {
  method: 'POST',
  headers: {
    'Accept': 'application/json',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  body: `vector=${JSON.stringify(vec)}&label=${JSON.stringify(label)}`
});
```
#### Response
```javascript
img: '' // base64 string
```
