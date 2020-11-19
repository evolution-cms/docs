### Здійснення редиректу на задану сторінку

```
bool|null sendRedirect(string $url, int $count_attempts = 0, string $type = '', string $responseCode = '')
```

**$url** - url сторінки, на яку буде здійснюватись редирект.

**$count_attempts** - додає 
лічильник кількості переадресацій в url. Можливі значення - '0', '1'. За замовчуванням - '0'.

**$type** - Тип редиректа. Можливі значення - 'REDIRECT_REFRESH' (негайна переадресація), 'REDIRECT_META' (переадресація засобами html), 'REDIRECT_HEADER' (редирект засобами php). За замовчуванням - пустий рядок, что дорівнює значенню 'REDIRECT_HEADER'.

**$responseCode** - код http-відповіді. Можливі значення: 'HTTP/1.1 301 Moved Permanently' - постійна переадресація; 'HTTP/1.1 302 Moved Temporarily' - тимчасова переадресація.


## Приклад:

**Виклик:**
```
return $modx->sendRedirect('url.html', 0, 'REDIRECT_HEADER', 'HTTP/1.1 301 Moved Permanently');
```

## Початковий код функції:
```
    /**
     * Redirect
     *
     * @param string $url
     * @param int $count_attempts
     * @param string $type $type
     * @param string $responseCode
     * @return bool|null
     * @global string $base_url
     * @global string $site_url
     */
    public function sendRedirect($url, $count_attempts = 0, $type = '', $responseCode = '')
    {
        $header = '';
        if (empty ($url)) {
            return false;
        }
        if ($count_attempts == 1) {
            // append the redirect count string to the url
            $currentNumberOfRedirects = isset ($_REQUEST['err']) ? $_REQUEST['err'] : 0;
            if ($currentNumberOfRedirects > 3) {
                $this->messageQuit('Redirection attempt failed - please ensure the document you\'re trying to redirect to exists. <p>Redirection URL: <i>' . $url . '</i></p>');
            } else {
                $currentNumberOfRedirects += 1;
                if (strpos($url, "?") > 0) {
                    $url .= "&err=$currentNumberOfRedirects";
                } else {
                    $url .= "?err=$currentNumberOfRedirects";
                }
            }
        }
        if ($type == 'REDIRECT_REFRESH') {
            $header = 'Refresh: 0;URL=' . $url;
        } elseif ($type == 'REDIRECT_META') {
            $header = '<META HTTP-EQUIV="Refresh" CONTENT="0; URL=' . $url . '" />';
            echo $header;
            exit;
        } elseif ($type == 'REDIRECT_HEADER' || empty ($type)) {
            // check if url has /$base_url
            global $base_url, $site_url;
            if (substr($url, 0, strlen($base_url)) == $base_url) {
                // append $site_url to make it work with Location:
                $url = $site_url . substr($url, strlen($base_url));
            }
            if (strpos($url, "\n") === false) {
                $header = 'Location: ' . $url;
            } else {
                $this->messageQuit('No newline allowed in redirect url.');
            }
        }
        if ($responseCode && (strpos($responseCode, '30') !== false)) {
            header($responseCode);
        }

        if(!empty($header)) {
            header($header);
        }

        exit();
    }	
```
