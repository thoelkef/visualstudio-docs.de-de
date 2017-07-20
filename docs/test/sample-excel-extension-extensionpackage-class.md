---
title: "Beispiel für Excel-Erweiterung: ExtensionPackage-Klasse | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 20e3ac96d5b12002b11a9e93b413c48738f57153
ms.contentlocale: de-de
ms.lasthandoff: 05/19/2017

---
# <a name="sample-excel-extension-extensionpackage-class"></a>Sample Excel Extension: ExtensionPackage Class
Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>-Klasse und stellt den Einstiegspunkt für einen Test der programmierten UI bereit, bei dem ein [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Arbeitsblatt getestet wird.  
  
## <a name="assembly-attribute"></a>Assembly-Attribut  
 Die Datei beginnt mit einem Assemblyattribut, das die Assembly als UI-Testerweiterung identifiziert.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Dieses Attribut deklariert den Basisklassennamen, den Namen der Paketklasse und den vollqualifizierten Klassennamen für die benutzerdefinierte Erweiterungspaketklasse.  
  
## <a name="simple-properties"></a>Einfache Eigenschaften  
 Die in dieser Klasse enthaltenen Eigenschaften stellen Werte bereit, die vom Framework für den Test der programmierten UI zum Identifizieren und Beschreiben der Erweiterung und der Assembly verwendet werden. Weitere Informationen finden Sie in den Codekommentaren.  
  
## <a name="getservice-method"></a>GetService-Methode  
 Die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>-Methode ist der einzige Einstiegspunkt, der vom Framework für den Test der programmierten UI verwendet wird, um entsprechend den Angaben in der Basisklasse für jedes Objekt Zugriff auf den Technologie-Manager, den Eigenschaftenanbieter und den Aktionsfilter zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

