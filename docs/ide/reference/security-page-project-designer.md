---
title: "Seite &quot;Sicherheit&quot;, Projekt-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Projekt-Designer, Seite „Sicherheit“"
  - "Seite „Sicherheit“ im Projekt-Designer"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Seite &quot;Sicherheit&quot;, Projekt-Designer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Über die Seite **Sicherheit** des **Projekt\-Designers** werden Sicherheitseinstellungen für den Codezugriff für Anwendungen konfiguriert, die über die [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)]\-Bereitstellung bereitgestellt werden.  Weitere Informationen finden Sie unter [Codezugriffssicherheit für ClickOnce\-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Klicken Sie zum Aufrufen der Seite **Sicherheit** auf einen Projektknoten im **Projektmappen\-Explorer**, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**.  
  
## Sicherheitseinstellungen  
 **ClickOnce\-Sicherheitseinstellungen aktivieren**  
 Bestimmt, ob Sicherheitseinstellungen zur Entwurfszeit aktiviert werden.  Wenn diese Option deaktiviert ist, sind alle anderen Optionen auf der Seite **Sicherheit** nicht verfügbar.  
  
> [!NOTE]
>  Wenn Sie eine Anwendung über den **Webpublishing**\-Assistenten veröffentlichen, wird diese Option automatisch aktiviert.  
  
 Wenn Sie diese Option auswählen, haben Sie die Wahl zwischen zwei Optionsfeldern: **Voll vertrauenswürdige Anwendung** oder **Teilweise vertrauenswürdige Anwendung**.  
  
 Standardmäßig ist diese Option bei WPF\-Webbrowseranwendungsprojekten aktiviert.  
  
 Für alle anderen Projekttypen ist diese Option standardmäßig deaktiviert.  
  
 **Voll vertrauenswürdige Anwendung**  
 Wenn Sie diese Option auswählen, fordert die Anwendung bei der Installation oder Ausführung auf einem Clientcomputer Berechtigungen für volle Vertrauenswürdigkeit an.  Verwenden Sie die Einstellung für volle Vertrauenswürdigkeit möglichst selten, da sie der Anwendung einen uneingeschränkten Zugriff auf Ressourcen wie Dateisystem und Registrierung gewährt.  
  
 Standardmäßig ist diese Option bei WPF\-Webbrowseranwendungsprojekten auf teilweise vertrauenswürdig eingestellt.  
  
 Standardmäßig ist diese Option für alle anderen Projekttypen auf Volle Vertrauenswürdigkeit eingestellt.  
  
 **Teilweise vertrauenswürdige Anwendung**  
 Wenn Sie diese Option auswählen, fordert die Anwendung bei der Installation oder Ausführung auf einem Clientcomputer Berechtigungen für teilweise Vertrauenswürdigkeit an.  *Teilweise Vertrauenswürdigkeit* bedeutet, dass nur die Aktionen, die unter den angeforderten Codezugriffssicherheitsberechtigungen erlaubt werden, ausgeführt werden.  Weitere Informationen zum Konfigurieren von Sicherheitsberechtigungen finden Sie unter [Codezugriffssicherheit für ClickOnce\-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Sie können die Sicherheitseinstellungen für teilweise Vertrauenswürdigkeit durch Konfigurieren der Optionen im Bereich **ClickOnce\-Sicherheitsberechtigungen** angeben.  
  
## ClickOnce\-Sicherheitsberechtigungen  
 **Zone, aus der die Anwendung installiert wird**  
 Gibt einen Standardsatz mit Berechtigungen für die Codezugriffssicherheit an.  Wählen Sie für einen beschränkten Berechtigungssatz die Optionen **Internet** oder **Lokales Intranet** aus, oder wählen Sie **\(Benutzerdefiniert\)** aus, um einen benutzerdefinierten Satz von Berechtigungen zu konfigurieren.  Wenn die Anwendung mehr Berechtigungen anfordert, als in einer Zone gewährt werden, wird eine ClickOnce\-Vertrauenseingabeaufforderung angezeigt, damit der Endbenutzer die zusätzlichen Berechtigungen gewähren kann.  Weitere Informationen zum Konfigurieren von Sicherheitsberechtigungen finden Sie unter [Codezugriffssicherheit für ClickOnce\-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Standardmäßig ist diese Option bei WPF\-Webbrowseranwendungsprojekten auf **Internet** eingestellt.  
  
 **XML\-Datei für Berechtigungen bearbeiten**  
 Öffnet die Anwendungsmanifestvorlage \(app.manifest\), um die Berechtigungen für den Berechtigungssatz **\(Benutzerdefiniert\)** zu konfigurieren.  
  
 **Erweitert**  
 Öffnet das [Dialogfeld "Erweiterte Sicherheitseinstellungen"](../../ide/reference/advanced-security-settings-dialog-box.md), das verwendet wird, um Einstellungen zum Debuggen der Anwendung mit beschränkten Berechtigungen zu konfigurieren.  Diese Einstellungen werden während des Debuggings überprüft, und Berechtigungsausnahmen geben an, dass die Anwendung möglicherweise mehr Berechtigungen benötigt, als in einer Zone definiert sind.  
  
## Siehe auch  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../../deployment/code-access-security-for-clickonce-applications.md)   
 [How to: Enable ClickOnce Security Settings](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce\-Anwendung](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce\-Anwendung mit eingeschränkten Berechtigungen](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)   
 [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)   
 [Dialogfeld "Erweiterte Sicherheitseinstellungen"](../../ide/reference/advanced-security-settings-dialog-box.md)