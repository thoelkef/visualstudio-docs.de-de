---
title: Beispiel für Excel-Communicator-Schnittstelle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660489"
---
# <a name="sample-excel-communicator-interface"></a>Beispiel für Excel-Communicator-Schnittstelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die beispielhafte `IExcelUICommunication`-Schnittstelle wird im `ExcelUICommunicator`-Objekt im `ExcelAddIn`-Projekt verwendet.

## <a name="iexceluicommunication-interface"></a>IExcelUICommunication-Schnittstelle
 Diese Schnittstelle definiert die Kommunikationspunkte zwischen `CodedUIExtension`, die im codierten UI-Testprozess und `ExcelCodedUIAddIn`, die im [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]-Prozess ausgeführt wird.

 Die `ExcelCodedUIAddinHelper`-Assembly verfügt über eine `ExcelUICommunicator`-Klasse, die von dieser Schnittstelle abgeleitet wird und das Excel-Objektmodell verwendet, um die Methoden zu verarbeiten.

 Einige Methoden rufen die angeforderten Informationen aus Excel auf und erstellen und geben eines der Informationsobjekte zurück, z.B. das `CellInformation`-Objekt.

 Andere Methoden verwenden ein bereitgestelltes Informationsobjekt, suchen das entsprechende Steuerelement in Excel und führen einen Prozess für das Steuerelement aus. Zum Beispiel führt die `ScrollIntoView`-Methode einen Bildlauf im Arbeitsblatt aus, damit die festgelegte Zelle sichtbar ist.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample und ExcelCodedUIAddinHelper-Kommunikation
 Die `ExcelCodedUIAddinHelper`-Assembly wird im Excel-Prozess ausgeführt und enthält die `UICommunicator`-Klasse, die die `IExcelUITestCommunication`-Schnittstelle implementiert und ruft die erforderliche Informationen direkt von der Excel-Benutzeroberfläche auf oder legt sie dort ab.

 Die `CodedUIExtensibilitySample`-Assembly wird im codierten UI-Testprozess von Visual Studio ausgeführt. Diese Assembly verfügt über die `Communicator`-Klasse, die einen .NET Remoting-Kanal öffnet und eine `Instance`-Eigenschaft zur Verfügung stellt, die die `IExcelUICommunication`-Schnittstelle verwendet, um das `UICommunicator`-Objekt in der `ExcelCodedUIAddinHelper`-Assembly zu verwenden, um Anforderungen und Informationsobjekte, wie z.B. ein `CellInformation`-Objekt zwischen den beiden Assemblys zu übergeben.

## <a name="see-also"></a>Weitere Informationen
 Erweitern von Tests der programmierten [UI und Aktions Aufzeichnungen zur Unterstützung des Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) - [Beispiel-Excel-Add-Ins für Tests](../test/sample-excel-add-in-for-coded-ui-testing.md) der programmierten UI [für Excel](../test/sample-coded-ui-test-extension-for-excel.md)
