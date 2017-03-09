---
title: "MSBuild Error MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3482
**MSB3482: Fehler beim Signieren: „\<Fehler\>“.**  
  
 Wenn Sie die ClickOnce\-Bereitstellung zum Veröffentlichen oder „SignTool“ zum Signieren von Manifesten verwenden, kann dieser Fehler auftreten, der von „SignTool“ generiert wird. Hier werden häufig auftretende Probleme aufgeführt.  
  
 **Fehler beim Signieren: „Der Wert darf nicht Null sein. Parametername: strongNameKey“.**  
  
 Dieser Fehler kann während der ClickOnce\-Bereitstellung in der Fehlerliste angezeigt werden. Das Problem wird durch Auswählen eines ungültigen Signaturschlüssels verursacht. In der Regel versuchen Sie einen Schlüssel zu verwenden, der nicht mit RSA verschlüsselt ist. „SignTool“ unterstützt lediglich die RSA\-Schlüsselverschlüsselung.  
  
 Rufen Sie einen Schlüssel mit RSA\-Verschlüsselung ab, für den Codesignaturen aktiviert sind, um diesen Fehler zu beheben.  
  
 **Fehler beim Signieren: „Eine Zertifikatkette zu einer vertrauenswürdigen Stammzertifizierungsstelle konnte nicht aufgebaut werden.“**  
  
 Dieser Fehler kann während der ClickOnce\-Bereitstellung in der Fehlerliste angezeigt werden. Das Problem ist, dass das Zertifikat eine Kette oder Stammzertifizierungsstelle aufweist, die auf dem Computer des Benutzers als nicht vertrauenswürdig eingestuft wird. Dies tritt normalerweise auf, wenn Zertifikate oder Schlüssel zwischen Computern verschoben werden.  
  
 Installieren Sie das „Stammzertifikat“ der Zertifizierungsstelle, die das Zertifikat erstellt hat, um diesen Fehler zu beheben. Normalerweise wechseln Sie zur Website des Zertifizierungsstellenanbieters und laden das Zertifikat bei Bedarf erneut herunter.  
  
 **Fehler beim Signieren: „Fehler beim Signieren von ...\\setup.exe. SignTool Error: ISignCode::Sign hat folgenden Fehler zurückgegeben: 0x80880253  Das Zertifikat des Signaturgebers ist nicht gültig für das Signieren.“**  
  
 Dieser Fehler kann während der ClickOnce\-Bereitstellung in der Fehlerliste angezeigt werden.  
  
 Das Problem wird wahrscheinlich dadurch verursacht, dass das Zertifikat nicht innerhalb des gültigen Bereichs liegt \(wenn Sie z. B. ein abgelaufenes Zertifikat verwenden\).  
  
 Rufen Sie ein aktualisiertes Zertifikat mit gültigem Datum ab, um diesen Fehler zu beheben.  
  
 Informationen zum Aktualisieren des Zertifikats finden Sie im Artikel 925521 „Sie erhalten bei dem Versuch, eine ClickOnce\-Anwendung von Visual Studio 2005 zu aktualisieren, eine Fehlermeldung, nachdem das zum Signieren der Installation verwendete Zertifikat abgelaufen ist“ in der Microsoft Knowledge Base unter [http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521).  
  
 **Der Keyset ist nicht vorhanden.**  
  
 Möglicherweise liegt ein Konflikt zwischen der PFX\-Datei und dem Zertifikat vor. Versuchen Sie, das Zertifikat zu löschen und erneut zu installieren und\/oder die PFX\-Datei neu zu erstellen.  
  
 **Schlüssel ist im angegebenen Status nicht gültig.**  
  
 Weitere Informationen finden Sie unter „http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx“.  
  
 **Der Parameter ist ungültig.**  
  
 Wird der Build nicht mit dem Dienst oder Benutzerkonto ausgeführt, mit dem das Zertifikat importiert wurde? Versuchen Sie, alle Einstellungen für lokale Sicherheitsrichtlinien zu deaktivieren, die den Schutz privater Schlüssel erfordern.  Löschen Sie dann das Zertifikat für das Benutzerkonto des Builds, und importieren Sie es anschließend erneut.  
  
 **Der angeforderte Vorgang kann nicht abgeschlossen werden.  Dem Computer muss zu Delegierungszwecken vertraut werden, und das aktuelle Benutzerkonto muss so konfiguriert sein, dass es die Delegierung gestattet.**  
  
 Weitere Informationen finden Sie in diesem [MSDN\-Blogbeitrag](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx).  
  
## Siehe auch  
 [Einführung in die Codesignatur](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(Sign Tool\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [Seite "Signierung", Projekt\-Designer](../ide/reference/signing-page-project-designer.md)   
 [Gewusst wie: Signieren einer Assembly \(Visual Studio\)](http://msdn.microsoft.com/de-de/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Assemblys mit starkem Namen](../Topic/Strong-Named%20Assemblies.md)   
 [Signieren mit starkem Namen für verwaltete Anwendungen](http://msdn.microsoft.com/de-de/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)