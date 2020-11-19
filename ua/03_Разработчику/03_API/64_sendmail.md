### Функція надсилання пошти через API Evolution CMS 

Відправляє пошту за допомогою способа, що вказаний на панелі керування сайтом.
```
$modx->sendmail()
```

## Приклади використання ##

### Простий варіант:
```
   		$param = array();
		$param['from']    = "{$site_name}<{$emailsender}>";
		$param['subject'] = $emailsubject;
		$param['body']    = $message;
		$param['to']      = $email;
		$rs = $modx->sendmail($param);
```

### Варіант з розширеними налаштуваннями:

```
		$modx->loadExtension('MODxMailer');
		$modx->mail->IsHTML($isHtml);
		$modx->mail->From	= $from;
		$modx->mail->FromName	= $fromname;
		$modx->mail->Subject	= $subject;
		$modx->mail->Body	= $report;
		AddAddressToMailer($modx->mail,"replyto",$replyto);
		AddAddressToMailer($modx->mail,"to",$to);
		AddAddressToMailer($modx->mail,"cc",$cc);
		AddAddressToMailer($modx->mail,"bcc",$bcc);
		AttachFilesToMailer($modx->mail,$attachments);
		if(!$modx->mail->send()) return 'Main mail: ' . $_lang['ef_mail_error'] . $modx->mail->ErrorInfo;
 ```
 Значення деяких з полей (до прикладу, From и Fromname) при ініціалізації ModxMailer підставляються з конфігурації сайту. При необхідності їх можна скоротити.