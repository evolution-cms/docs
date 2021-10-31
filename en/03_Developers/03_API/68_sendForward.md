Загружает выбранный ресурс не изменяя URL страницы

```
null sendForward(int $id, string $responseCode = '')
```

**$id** - id ресурса, который будет загружен

**$responseCode** - код http-ответа. Возможные значения - 'HTTP/1.1 301 Moved Permanently', 'HTTP/1.1 302 Moved Temporarily' (постоянная и временная переадресация соответственно).


## Пример:

**Вызов:**

```
return $modx->sendForward(5);
```

с передачей заголовка с кодом http-ответа:
```
return $modx->sendForward(5, 'HTTP/1.1 301 Moved Permanently');
```

## Исходный код функции
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
