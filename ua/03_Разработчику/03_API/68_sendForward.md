### Завантаження вибраного ресурсу без змінення URL сторінки

```
null sendForward(int $id, string $responseCode = '')
```

**$id** - id ресурсу, який потрібно завантажити.

**$responseCode** - код http-відповіді. Можливі значення: 'HTTP/1.1 301 Moved Permanently' - постійна переадресація; 'HTTP/1.1 302 Moved Temporarily' - тимчасова переадресація.


## Приклад:

**Виклик:**

```
return $modx->sendForward(5);
```

Із передаванням заголовка з кодом http-відповіді:
```
return $modx->sendForward(5, 'HTTP/1.1 301 Moved Permanently');
```

## Початковий код функції:
```
    /**
     * Forward to another page
     *
     * @param int|string $id
     * @param string $responseCode
     */
    public function sendForward($id, $responseCode = '')
    {
        if ($this->forwards > 0) {
            $this->forwards = $this->forwards - 1;
            $this->documentIdentifier = $id;
            $this->documentMethod = 'id';
            if ($responseCode) {
                header($responseCode);
            }
            $this->prepareResponse();
            exit();
        } else {
            $this->messageQuit("Internal Server Error id={$id}");
            header('HTTP/1.0 500 Internal Server Error');
            die('<h1>ERROR: Too many forward attempts!</h1><p>The request could not be completed due to too many unsuccessful forward attempts.</p>');
        }
    }
```
