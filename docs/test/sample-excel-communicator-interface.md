---
title: Beispiel für Excel-Communicator-Schnittstelle
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88aa282a2e742ffff53582fd4855d06e3a06db69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-communicator-interface"></a>Beispiel für Excel-Communicator-Schnittstelle
Die beispielhafte `IExcelUICommunication`-Schnittstelle wird im `ExcelUICommunicator`-Objekt im `ExcelAddIn`-Projekt verwendet.

## <a name="iexceluicommunication-interface"></a>IExcelUICommunication-Schnittstelle
 Diese Schnittstelle definiert die Kommunikationspunkte zwischen `CodedUIExtension`, die im codierten UI-Testprozess und `ExcelCodedUIAddIn`, die im [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Prozess ausgeführt wird.

 Die `ExcelCodedUIAddinHelper`-Assembly verfügt über eine `ExcelUICommunicator`-Klasse, die von dieser Schnittstelle abgeleitet wird und das Excel-Objektmodell verwendet, um die Methoden zu verarbeiten.

 Einige Methoden rufen die angeforderten Informationen aus Excel auf und erstellen und geben eines der Informationsobjekte zurück, z.B. das `CellInformation`-Objekt.

 Andere Methoden verwenden ein bereitgestelltes Informationsobjekt, suchen das entsprechende Steuerelement in Excel und führen einen Prozess für das Steuerelement aus. Zum Beispiel führt die `ScrollIntoView`-Methode einen Bildlauf im Arbeitsblatt aus, damit die festgelegte Zelle sichtbar ist.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample und ExcelCodedUIAddinHelper-Kommunikation
 Die `ExcelCodedUIAddinHelper`-Assembly wird im Excel-Prozess ausgeführt und enthält die `UICommunicator`-Klasse, die die `IExcelUITestCommunication`-Schnittstelle implementiert und ruft die erforderliche Informationen direkt von der Excel-Benutzeroberfläche auf oder legt sie dort ab.

 Die `CodedUIExtensibilitySample`-Assembly wird im codierten UI-Testprozess von Visual Studio ausgeführt. Diese Assembly verfügt über die `Communicator`-Klasse, die einen .NET Remoting-Kanal öffnet und eine `Instance`-Eigenschaft zur Verfügung stellt, die die `IExcelUICommunication`-Schnittstelle verwendet, um das `UICommunicator`-Objekt in der `ExcelCodedUIAddinHelper`-Assembly zu verwenden, um Anforderungen und Informationsobjekte, wie z.B. ein `CellInformation`-Objekt zwischen den beiden Assemblys zu übergeben.

## <a name="see-also"></a>Siehe auch

- [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Beispiel-Excel-Add-In für Test der programmierten UI](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Beispielerweiterung für Tests der programmierten Benutzeroberfläche für Excel](../test/sample-coded-ui-test-extension-for-excel.md)
