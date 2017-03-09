---
title: "Problembehandlung von Ausnahmen zur Codezugriffssicherheit | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CodeAccessPermission-Klasse"
  - "CodeAccessSecurityException-Klasse"
  - "Codezugriffssicherheit, Problembehandlung"
  - "Sicherheit [Debugger], Problembehandlung Codezugriffssicherheit"
  - "Problembehandlung Codezugriffssicherheit"
ms.assetid: ca368d3b-f6d0-4c89-af59-d94f343fca35
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung von Ausnahmen zur Codezugriffssicherheit
Über Berechtigungen wird gesteuert, was Code tun darf. Zum Ausführungszeitpunkt wird der Anwendung durch die Laufzeit ein Berechtigungssatz zugewiesen. Wenn die Anwendung über ausreichende Berechtigungen verfügt, wird sie ordnungsgemäß ausgeführt; andernfalls wird eine Sicherheitsausnahme ausgelöst.  
  
 Welche Berechtigungen dem Code eingeräumt werden, hängt davon ab, von wo aus die Anwendung gestartet wird \(etwa aus dem Internet, aus einem Intranet oder auf dem lokalen Computer\) und mit welchen Sicherheitseinstellungen der Computer konfiguriert ist, auf dem die Anwendung ausgeführt wird. Da diese Einstellungen auf jedem Computer unterschiedlich sein können, lässt sich nicht grundsätzlich vorhersagen, ob der Code ausreichende Berechtigungen erhält.  
  
 Durch das Anfordern von Berechtigungen wird sichergestellt, dass der Code ausgeführt wird, sofern die Sicherheitsrichtlinien auf dem lokalen Computer dies zulassen. Wenn Sie die notwendigen Berechtigungen nicht anfordern, riskieren Sie, dass der Code nicht ausgeführt wird. Weitere Informationen über Codezugriffsberechtigungen und deren Anforderung finden Sie unter [Codezugriffsberechtigungen](http://msdn.microsoft.com/de-de/e5ae402f-6dda-4732-bbe8-77296630f675) oder [NIB: Anfordern von Berechtigungen](http://msdn.microsoft.com/de-de/0447c49d-8cba-45e4-862c-ff0b59bebdc2). Weitere Informationen über `Try...Catch`\-Blöcke finden Sie unter [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen können im Anwendungs\-Designer über die Seite Sicherheit bei Bedarf zusätzliche Berechtigungen anfordern. Weitere Informationen finden Sie unter [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Zu den möglichen Ursachen für Ausnahmen zur Codezugriffssicherheit zählen:  
  
-   **Zwischenablage.** Programmgesteuertes Einfügen aus der Zwischenablage ist ein eingeschränktes Feature von verwaltetem Code, da die Zwischenablage möglicherweise vertrauliche Informationen enthält.  
  
-   **Zugriff auf Registrierung oder Dateisystem.** Der Zugriff auf das lokale Dateisystem ist eingeschränkt. Wenn Sie auf eine Datei oder Ressource zugreifen, die mit der Assembly bereitgestellt wird, verwenden Sie `Assembly.GetExecutingAssembly.Location`, um den Pfad zu der Assembly abzurufen.  
  
-   **Netzwerkzugriff.** Stellen Sie sicher, dass die Assembly genau das Protokoll verwendet, mit dem sie auch geladen wurde. Im Allgemeinen wird Netzwerkkommunikation nur mit der URL zugelassen, von der die Assembly stammt.  
  
-   **Drucken.** Software, die in der Internetzone ausgeführt wird, kann nur über ein Standarddialog drucken. Wenn die Software einen Standarddialog verwendet, in dem der Benutzer einen Drucker auswählen kann, ist die Auswahl auf die Verwendung des Standarddruckers beschränkt.  
  
-   **Serialisierung.** Nur Code, der als voll vertrauenswürdig eingestuft ist, kann ein Objekt aus beliebigen Daten neu erstellen. Für die XML\-Serialisierung sollte der `XmlSerializer`\-Typ von teilweise vertrauenswürdigem Code technisch verwendet werden können. Weitere Informationen zum `XmlSerializer`\-Typ finden Sie unter [XmlSerializer\-Klasse](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx).  
  
-   **Reflektion.** Viele der reflektionsbezogenen Features der Laufzeit sind von der Verwendung durch teilweise vertrauenswürdigen Code ausgeschlossen.  
  
## Testen von Code, um zu bestimmen, ob eine Ausnahme zur Codezugriffssicherheit ausgelöst wird  
 Für einen Codeblock, der eventuell eine `CodeAccessSecurityException` auslöst, sollten Sie einen `Try...Catch`\-Block verwenden. Damit können Sie den Code in angepasster Weise ausführen und evtl. auftretende Probleme umgehen.  
  
 Möglicherweise möchten Sie die Anwendung so gestalten, dass sich ihr Verhalten an den vom Hostsystem eingeräumten Berechtigungen ausrichtet. Beispielsweise wäre es sinnvoll, einen Druckbefehl in einem Menü zu deaktivieren, wenn die Anwendung nicht zum Drucken berechtigt ist.  
  
 Um dies zu testen, können Sie eine Instanz einer von `CodeAccessPermission` abgeleiteten Klasse erstellen, z. B. `FileIOPermission`. Sie können dann innerhalb eines `Demand`\-Blocks die `Try...Catch`\-Methode auf die Berechtigung anwenden. Wenn die Ausnahme ausgelöst wird, verfügt die Assembly nicht über die Berechtigung.  
  
 Das folgende Beispiel testet, ob die Assembly die `EventLogPermission`\-Berechtigung besitzt. Dazu wird zunächst eine `EventLogPermission` ausgeführt oder erstellt. Dann wird innerhalb eines `Demand`\-Blocks die zugehörige `Try...Catch`\-Methode ausgeführt, um zu bestimmen, ob `Demand` erfolgreich ist.  
  
```  
Try Dim MyPermission As New EventLogPermission MyPermission.Demand() MsgBox(MyPermission.ToString()) Catch ex As Exception MsgBox("Assembly lacks EventLogPermission.") End Try  
```  
  
## Siehe auch  
 [Codezugriffsberechtigungen](http://msdn.microsoft.com/de-de/e5ae402f-6dda-4732-bbe8-77296630f675)   
 [NIB: Anfordern von Berechtigungen](http://msdn.microsoft.com/de-de/0447c49d-8cba-45e4-862c-ff0b59bebdc2)   
 [Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)