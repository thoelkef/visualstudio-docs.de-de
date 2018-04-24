---
title: 'Beispiel für Excel-Erweiterung: ExtensionPackage-Klasse | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 623b18a22441fdd2478716582d94a8b878c31d54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
