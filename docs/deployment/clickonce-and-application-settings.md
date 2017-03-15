---
title: "ClickOnce and Application Settings | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, application settings"
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce and Application Settings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit den Anwendungseinstellungen für Windows Forms wird das Erstellen, Speichern und Verwalten von benutzerdefinierten Einstellungen für Anwendungen und Benutzer auf dem Client erleichtert.  Das vorliegende Dokument erläutert, wie Anwendungseinstellungsdateien in einer ClickOnce\-Anwendung funktionieren und wie ClickOnce Einstellungen migriert, wenn der Benutzer auf eine nachfolgende Version aktualisiert.  
  
 Die im Folgenden gegebenen Informationen gelten nur für den Standardanbieter von Anwendungseinstellungen, die <xref:System.Configuration.LocalFileSettingsProvider>\-Klasse.  Wenn Sie einen benutzerdefinierten Anbieter bereitstellen, wird in diesem Anbieter festgelegt, wie die Daten gespeichert und bei einem Versionswechsel aktualisiert werden.  Weitere Informationen zu Anbietern von Anwendungseinstellungen finden Sie unter [Architektur der Anwendungseinstellungen](../Topic/Application%20Settings%20Architecture.md).  
  
## Anwendungseinstellungsdateien  
 Anwendungseinstellungen nutzen zwei Dateien: "*Anwendung*.exe.config" und "user.config", wobei *Anwendung* für den Namen der Windows Forms\-Anwendung steht.  "user.config" wird auf dem Client erstellt, wenn die Anwendung zum ersten Mal benutzerspezifische Einstellungen speichert.  "*Anwendung*.exe.config" ist dagegen schon vor der Bereitstellung vorhanden, wenn Sie Standardwerte für Einstellungen definieren.  Visual Studio berücksichtigt diese Datei automatisch, wenn Sie den Befehl **Veröffentlichen** verwenden.  Wenn Sie eine ClickOnce\-Anwendung mit Mage.exe oder MageUI.exe erstellen, müssen Sie sicherstellen, dass diese Datei zusammen mit den anderen Dateien der Anwendung in das Anwendungsmanifest aufgenommen wird.  
  
 In einer Windows Forms\-Anwendung, die nicht mit ClickOnce bereitgestellt wurde, wird die Datei *app*.exe.config einer Anwendung im Anwendungsverzeichnis gespeichert. Die Datei user.config wird im Ordner **Dokumente und Einstellungen** des Benutzers gespeichert.  In einer ClickOnce\-Anwendung befindet sich die Datei *app*.exe.config im Anwendungsverzeichnis des ClickOnce\-Anwendungscaches, und user.config befindet sich im ClickOnce\-Datenverzeichnis für diese Anwendung.  
  
 Unabhängig davon, wie Sie die Anwendung bereitstellen, ist bei den Anwendungseinstellungen ein sicherer Lesezugriff auf *app*.exe.config und ein sicherer Schreib\-\/Lesezugriff auf user.config sichergestellt.  
  
 In einer ClickOnce\-Anwendung wird die Größe der von den Anwendungseinstellungen verwendeten Konfigurationsdateien durch die Größe des ClickOnce\-Caches beschränkt.  Weitere Informationen finden Sie unter [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md).  
  
## Versionsupgrades  
 Genau wie jede Version einer ClickOnce\-Anwendung von allen anderen Versionen getrennt ist, sind die Anwendungseinstellungen einer ClickOnce\-Anwendung getrennt von den Einstellungen der anderen Versionen.  Wenn ein Benutzer die Anwendung auf eine neuere Version aktualisiert, vergleichen die Anwendungseinstellungen die Einstellungen der neuesten Version \(mit der höchsten Versionsnummer\) mit den Einstellungen, die mit der aktualisierten Version bereitgestellt werden. Anschließend werden die Einstellungen in einem neuen Satz Einstellungsdateien zusammengeführt.  
  
 Die folgende Tabelle beschreibt, wie in den Anwendungseinstellungen entschieden wird, welche Einstellungen kopiert werden.  
  
|Art der Änderung|Upgradeaktion|  
|----------------------|-------------------|  
|Einstellung wurde *app*.exe.config hinzugefügt|Die neue Einstellung wird in *app*.exe.config der aktuellen Version aufgenommen.|  
|Einstellung wurde aus *app*.exe.config entfernt|Die alte Einstellung wird aus *app*.exe.config der aktuellen Version entfernt.|  
|Standardwert der Einstellung wurde geändert; lokale Einstellung in user.config ist immer noch auf den ursprünglichen Standardwert festgelegt|Die Einstellung wird in user.config der aktuellen Version aufgenommen und erhält den neuen Standardwert als Wert.|  
|Standardwert der Einstellung wurde geändert; Einstellung in user.config ist nicht auf Standardwert festgelegt|Die Einstellung wird in user.config der aktuellen Version aufgenommen; der nicht dem Standardwert entsprechende Wert wird beibehalten.|  
  
 Wenn Sie eine eigene Wrapperklasse für die Anwendungseinstellungen erstellt haben und die Programmlogik für Updates anpassen möchten, können Sie die <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>\-Methode überschreiben.  
  
## ClickOnce und Roamingeinstellungen  
 ClickOnce funktioniert nicht mit Roamingeinstellungen, bei denen Ihnen die Einstellungsdatei auf allen Computern in einem Netzwerk zur Verfügung steht.  Wenn Sie Roamingeinstellungen benötigen, müssen Sie entweder einen Anbieter von Anwendungseinstellungen erstellen, bei den die Einstellungen über das Netzwerk gespeichert werden, oder eigene benutzerdefinierte Einstellungsklassen entwickeln, mit denen Einstellungen auf einem Remotecomputer gespeichert werden.  Weitere Informationen zu Einstellungsanbietern finden Sie unter [Architektur der Anwendungseinstellungen](../Topic/Application%20Settings%20Architecture.md).  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Übersicht über Anwendungseinstellungen](../Topic/Application%20Settings%20Overview.md)   
 [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md)   
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce\-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)