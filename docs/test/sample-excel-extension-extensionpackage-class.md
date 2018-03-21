---
title: "Beispiel für Excel-Erweiterung: ExtensionPackage-Klasse | Microsoft-Dokumentation"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2d4c7b5c3aefbc59b8e8931376f0bcf14951c9bc
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
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

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
