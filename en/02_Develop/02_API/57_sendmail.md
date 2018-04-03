###$modx->sendmail()
Method used for send mails by API (available since 1.0.12). Works with settings, sending emails using `mail()` or SMTP according to the specified settings in the manager panel.
Usage: 

####simple variant 
```
   		$param = array();
		$param['from']    = "{$site_name}<{$emailsender}>";
		$param['subject'] = $emailsubject;
		$param['body']    = $message;
		$param['to']      = $email;
		$rs = $modx->sendmail($param);
```	
####variant with additional settings 
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