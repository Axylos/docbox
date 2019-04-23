## SEI Drakey

This is a set of deployed JSON api's to provide sample backends for SEI-NYC

### Authentication

You can authenticate by navigating to [the drakey api](http://wdi_friends.draketalley.com/login/).

After either registering or logging in (`/register/` and `/login/`) respectively, the server will display an authentication token.  Save this somewhere.

All endpoints in the drakey api require an authentication token.  Include the token from above in each request by passing it as an *Authorization Bearer token*

#### Example Request

```curl
$ curl http://wdi_friends.draketalley.com/api/trains \
		-H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf'
```

```javascript
const token = 'asjkhdfkjhdf-384394-asdfkhasdkjf';

const api = axios.create({
  baseURL: 'http://wdi_friends.draketalley.com/api',
  headers: { Authorization: `Bearer ${token}` }
});


(async () => {
  try {
    const resp = await api.get('/trains');
    console.log(resp.data);
  } catch (e) {
    console.log(e.message);
  }
})();
```

In the examples, `asjkhdfkjhdf-384394-asdfkhasdkjf` would be the token retrieved from the login and register actions.  Feel free to interpolate it in the 