---
title: 'Beispiel für Excel-Erweiterung: ExtensionPackage-Klasse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672212"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Sample Excel Extension: ExtensionPackage Class
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>-Klasse und stellt den Einstiegspunkt für einen Test der programmierten UI bereit, bei dem ein [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]-Arbeitsblatt getestet wird.

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

## <a name="see-also"></a>Weitere Informationen
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
