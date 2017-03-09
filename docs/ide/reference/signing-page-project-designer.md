---
title: "Seite &quot;Signierung&quot;, Projekt-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.AddNewStrongNameKey"
  - "ResolveKeySource.KeyFileForSignAssemblyNotImported"
  - "vb.ProjectPropertiesSigning.ChangePasswordDialog"
  - "ResolveKeySource.KeyFileForManifestNotImported"
  - "vb.ProjectPropertiesSigning"
  - "vb.ProjectPropertiesSigning.PasswordNeededDialog"
  - "vb.ProjectPropertiesSigning.PfxPasswordDialog"
helpviewer_keywords: 
  - "Projekt-Designer, Seite „Signierung“"
  - "Seite „Signierung“ im Projekt-Designer"
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seite &quot;Signierung&quot;, Projekt-Designer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Signieren Sie die Anwendungs\- und Bereitstellungsmanifeste auf der Seite **Signierung** des **Projekt\-Designers**, und signieren Sie auch die Assembly \(Signierung mit starkem Namen\).  
  
 Beachten Sie, dass das Signieren von Anwendungs\- und Bereitstellungsmanifesten und das Signieren einer Assembly voneinander unabhängige Prozesse sind, obwohl beide auf der Seite **Signierung** erfolgen.  
  
 Außerdem erfolgt bei Manifestsignierung und Assemblysignierung das Speichern von Schlüsseldateiinformationen unterschiedlich.  Bei der Manifestsignierung werden Schlüsselinformationen in der kryptografischen Speicherdatenbank des Computers und dem Windows\-Zertifikatspeicher des aktuellen Benutzers gespeichert.  Bei der Assemblysignierung werden Schlüsselinformationen nur in der kryptografischen Speicherdatenbank des Computers gespeichert.  
  
 Wählen Sie zum Aufrufen der Seite **Signierung** einen Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Signierung**.  
  
## Signierung von Anwendungs\- und Bereitstellungsmanifesten  
 **ClickOnce\-Manifeste signieren** Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, um die Anwendungs\- und Bereitstellungsmanifeste mit einem öffentlichen\/privaten Schlüsselpaar zu signieren.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Signieren von Anwendungs\- und Bereitstellungsmanifesten](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 **Aus Speicher auswählen** Schaltfläche  
 Ermöglicht es Ihnen, ein vorhandenes Zertifikat aus dem persönlichen Zertifikatspeicher des aktuellen Benutzers auszuwählen.  Sie können eines dieser Zertifikate auswählen, um Anwendungs\- und Bereitstellungsmanifeste zu signieren.  
  
 Durch Klicken auf **Aus Speicher auswählenZertifikat auswählen** öffnet das Dialogfeld Zertifikate in Ihrem persönlichen Zertifikatspeicher auflistet, die gerade gültig sind \(nicht abgelaufen\), und der private Schlüssel verfügen.  Zu den Funktionen des ausgewählten Zertifikats sollten auch Codesignaturen gehören.  
  
 Wenn Sie auf **Zertifikateigenschaften anzeigen** klicken, wird das Dialogfeld **Zertifikatdetails**.  Dieses Dialogfeld stellt ausführliche Informationen über das Zertifikat ein und schließt zusätzliche Optionen ein.  Sie können auf **Weitere Informationen zu Zertifikaten** klicken, um zusätzliche Hilfeinformationen anzuzeigen.  
  
 **Aus Datei auswählen** Schaltfläche  
 Ermöglicht es Ihnen, ein Zertifikat aus einer vorhandenen Schlüsseldatei auszuwählen.  
  
 Durch Klicken auf **Aus Datei auswählen** öffnet das **Datei auswählen** Dialogfeld, in dem Sie eine Taste Zertifikat auszuwählen \(Personal Information Exchange\).  Die Datei muss kennwortgeschützt sein und darf nicht bereits in Ihrem persönlichen Zertifikatspeicher gefunden werden.  
  
 Im **Kennwort zum Öffnen der Datei eingeben** Dialogfeld geben Sie ein Kennwort ein, um die Datei der Zertifikats Schlüssel zu öffnen \(Personal Information Exchange\).  Die Kennwortinformationen werden in der persönlichen Schlüsselcontainerliste und dem persönlichen Zertifikatspeicher gespeichert.  
  
 **Testzertifikat erstellen** Schaltfläche  
 Ermöglicht es Ihnen, ein Zertifikat zum Testen zu erstellen.  Das Testzertifikat ist für das Signieren der ClickOnce\-Anwendung und Bereitstellungsmanifeste verwendet.  
  
 Durch Klicken auf **Testzertifikat erstellen** öffnet das **Testzertifikat erstellen** Dialogfeld, in dem Sie ein Kennwort für die Schlüsseldatei mit starkem Namen für das Testzertifikat eingeben können.  Die Datei ist mit *projectname*\_TemporaryKey.pfx benannt.  Wenn Sie auf **OK** klicken, ohne ein Kennwort einzugeben, ist die PFX\-Datei nicht das verschlüsselte Kennwort.  
  
 **Timestampserver\-URL** Feld  
 Gibt die Adresse eines Servers an, der die Signatur mit einem Zeitstempel versieht.  Wenn Sie ein Zertifikat bereitstellen, überprüft diese externe Site die Zeit, zu der die Anwendung signiert wurde.  
  
## Signieren von Assemblys  
 **Assembly signieren** Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, um die Assembly zu signieren und eine Schlüsseldatei mit starkem Namen zu erstellen.  Weitere Informationen über das Signieren der Assembly mit dem **Projekt\-Designer** finden Sie unter [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/de-de/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Diese Option verwendet zum Signieren der Assembly das von [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] bereitgestellte Tool Al.exe.  Weitere Informationen über Al.exe finden Sie unter [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
 **Schlüsseldatei mit starkem Namen auswählen** Liste  
 Ermöglicht es Ihnen, ein neues oder vorhandene Schlüsseldatei mit starkem Namen an, mit dem die Assembly signiert.  Wählen Sie zum Auswählen einer vorhandenen Schlüsseldatei die Option **\<Durchsuchen...\>** aus.  
  
 Wählen Sie  **\<Neu…\>**  aus, um eine neue Schlüsseldatei zu erstellen, mit der die Assembly signiert werden.  Das **Schlüssel für einen starken Namen erstellen** Dialogfeld wird angezeigt, das Sie verwenden können, um einen Dateinamen anzugeben und die Schlüsseldatei Schlüssel mit einem Kennwort geschützt werden soll.  Das Kennwort muss mindestens 6 Zeichen lang sein.  Wenn Sie ein Kennwort festlegen, wird eine PFX\-Datei \(Personal Information Exchange\) erstellt. Wenn Sie kein Kennwort festlegen, wird eine SNK\-Datei \(Strongly Named Key\) erstellt.  
  
 **Kennwort ändern** Schaltfläche  
 Ändert das Kennwort für die Schlüsseldatei des privaten Informationsaustauschs \(Personal Information Exchange\), die verwendet wird, um die Assembly zu signieren.  
  
 Durch Klicken auf **Kennwort ändern** öffnet das Dialogfeld **Schlüsselkennwort ändern**.  In diesem Dialogfeld wird **Altes Kennwort** das aktuelle Kennwort für die Schlüsseldatei.  **Neues Kennwort** wenige 6 Zeichen lang sein muss.  Die Kennwortinformationen werden im Windows\-Zertifikatspeicher des aktuellen Benutzers gespeichert.  
  
 **Nur verzögerte Signierung** Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, um die verzögerte Signierung zu aktivieren.  
  
 Beachten Sie, dass ein mit Verzögerung signiertes Projekt nicht ausgeführt und nicht gedebuggt werden kann.  Sie können jedoch das [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) mit der Option `-Vr` verwenden, um die Überprüfung bei der Entwicklung zu überspringen.  
  
> [!NOTE]
>  Wenn Sie eine Assembly signieren Sie möglicherweise nicht immer Zugriff auf einer privaten Schlüssel.  Zum Beispiel könnte eine Organisation genau ein Schlüsselpaar, abgesichertes keinen Zugriff auf den Entwickler täglich haben.  Der öffentliche Schlüssel verfügbar sein, aber der private Schlüssel wird mit einigen Personen beschränkt.  In diesem Fall müssen Sie eine *verzögerte* oder *teilweise Signierung* vornehmen, um zunächst den öffentlichen Schlüssel verfügbar zu machen. Das Hinzufügen des privaten Schlüssels wird bis zur Bereitstellung der Assembly verschoben.  
  
## Siehe auch  
 [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)   
 [Verwalten der Signierung von Assemblys und Manifesten](../../ide/managing-assembly-and-manifest-signing.md)   
 [Strong\-Name Signing for Managed Applications](http://msdn.microsoft.com/de-de/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Gewusst wie: Signieren von Anwendungs\- und Bereitstellungsmanifesten](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/de-de/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Assemblys mit starkem Namen](../Topic/Strong-Named%20Assemblies.md)