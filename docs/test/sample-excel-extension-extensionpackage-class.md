---
title: "Sample Excel Extension: ExtensionPackage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Sample Excel Extension: ExtensionPackage Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>\-Klasse und stellt den Einstiegspunkt für einen Test der codierten UI bereit, bei dem ein [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]\-Arbeitsblatt getestet wird.  
  
## Assemblyattribut  
 Die Datei beginnt mit einem Assemblyattribut, das die Assembly als UI\-Testerweiterung identifiziert.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Dieses Attribut deklariert den Basisklassennamen, den Namen der Paketklasse und den vollqualifizierten Klassennamen für die benutzerdefinierte Erweiterungspaketklasse.  
  
## Einfache Eigenschaften  
 Die in dieser Klasse enthaltenen Eigenschaften stellen Werte bereit, die vom Framework für den Test der codierten UI zum Identifizieren und Beschreiben der Erweiterung und der Assembly verwendet werden.  Weitere Informationen finden Sie in den Codekommentaren.  
  
## GetService\-Methode  
 Die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>\-Methode ist der einzige Einstiegspunkt, der vom Framework für den Test der codierten UI verwendet wird, um entsprechend den Angaben in der Basisklasse jedes Objekts Zugriff auf den Technologie\-Manager, den Eigenschaftenanbieter und den Aktionsfilter zu erhalten.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)