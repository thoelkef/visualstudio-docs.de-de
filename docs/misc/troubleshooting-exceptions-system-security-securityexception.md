---
title: "Problembehandlung bei Ausnahmen: System.Security.SecurityException | Microsoft Docs"
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
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException-Klasse"
  - "SecurityException-Klasse"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Security.SecurityException
Eine <xref:System.Security.SecurityException>\-Ausnahme wird ausgelöst, wenn ein Sicherheitsfehler erkannt wird.  
  
## Tipps  
 Passen Sie die Berechtigungsebene der Assembly auf der Eigenschaftenseite an.  
 Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>.  
  
 Anwendungsdaten in isoliertem Speicher speichern.  
 Isolierte Speicherung ist eine Datenspeicherung, die für Isolierung und Sicherheit sorgt, indem standardisierte Verknüpfungen von Code mit gespeicherten Daten definiert werden. Weitere Informationen finden Sie unter [Isolierte Speicherung](../Topic/Isolated%20Storage.md).  
  
 Verwenden Sie zum Öffnen oder Speichern einer Datei die <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>\-Methode, wenn Sie <xref:System.Windows.Forms.OpenFileDialog> verwenden.  
 Dadurch kann die Anwendung in einem teilweise vertrauenswürdigen Kontext ausgeführt werden.  
  
 Stellen Sie sicher, dass Lese\- und Schreibvorgänge der Anwendung für vorhandene Ereignisprotokolle auf dem lokalen Computer ausgeführt werden.  
 Die Anwendung verfügt möglicherweise nicht über die erforderlichen Berechtigungen, Protokolle zu erstellen oder auf nicht lokale Computer zu schreiben.  
  
 Wenn Sie nicht verwaltete Bibliotheken aufrufen, verwenden Sie entsprechende verwaltete Bibliotheken.  
 Eine entsprechende API ist möglicherweise im Framework vorhanden. Weitere Informationen finden Sie unter [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
 Sichere Fenster verwenden.  
 Die <xref:System.Security.Permissions.UIPermissionWindow>\-Enumeration gibt den Fenstertyp an, der von Code verwendet werden darf.  
  
 Gestatten Sie Benutzern, über die <xref:System.Windows.Forms.PrintDialog>\-Komponente zu drucken.  
 Dadurch kann die Anwendung in einem teilweise vertrauenswürdigen Kontext ausgeführt werden. Weitere Informationen finden Sie unter <xref:System.Windows.Forms.PrintDialog>.  
  
 Drucken Sie auf dem Standarddrucker.  
 Dadurch kann die Anwendung in einem teilweise vertrauenswürdigen Kontext ausgeführt werden. Sie versuchen möglicherweise, auf einen Drucker zuzugreifen, für den Sie keine Zugriffsrechte haben.  
  
 Rufen Sie Daten von demselben Webserver ab, von dem sie bereitgestellt wurden.  
 Dadurch kann die Anwendung in einem teilweise vertrauenswürdigen Kontext ausgeführt werden.  
  
 Stellen Sie bei der Bereitstellung einer Office\-Lösung sicher, dass Sie alle erforderlichen Sicherheitsanforderungen erfüllt haben.  
 Weitere Informationen finden Sie unter [Überlegungen zur Sicherheit von Office\-Projektmappen](/office-dev/office-dev/specific-security-considerations-for-office-solutions).  
  
 Wenn eine Assembly, die das benutzerdefinierte Sicherheitsobjekt implementiert, auf andere Assemblys verweist, müssen Sie die betreffenden Assemblys der Liste voll vertrauenswürdiger Assemblys hinzufügen.  
 Weitere Informationen finden Sie unter [Caspol.exe \(Code Access Security Policy Tool\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md).  
  
## Siehe auch  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)