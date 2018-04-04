###$modx->sendmail()
Функция отправки почты через API(доступен с версии 1.0.12), удобен тем что работает в связке с настройками тоесть отправляет почту через mail() или SMTP в зависимости от указанных настроек в панели управления. 
Пример использования: 

####простой вариант 
```
   		$param = array();
		$param['from']    = "{$site_name}<{$emailsender}>";
		$param['subject'] = $emailsubject;
		$param['body']    = $message;
		$param['to']      = $email;
		$rs = $modx->sendmail($param);
```	
####вариант с расширенными настройками  
```
		$modx->loadExtension('MODxMailer');
		$modx->mail->IsHTML($isHtml);
		$modx->mail->From		= $from;
		$modx->mail->FromName	= $fromname;
		$modx->mail->Subject	= $subject;
		$modx->mail->Body		= $report;
		AddAddressToMailer($modx->mail,"replyto",$replyto);
		AddAddressToMailer($modx->mail,"to",$to);
		AddAddressToMailer($modx->mail,"cc",$cc);
		AddAddressToMailer($modx->mail,"bcc",$bcc);
		AttachFilesToMailer($modx->mail,$attachments);
		if(!$modx->mail->send()) return 'Main mail: ' . $_lang['ef_mail_error'] . $modx->mail->ErrorInfo;
 ```