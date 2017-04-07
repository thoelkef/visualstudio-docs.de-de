---
title: "Beispiel für Excel-Communicator-Schnittstelle | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 58423d52947c920d42c91508922e5a84ef239b23
ms.lasthandoff: 04/04/2017

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
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel (Erweitern von programmierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel)](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Sample Excel Add-In for Coded UI Testing (Beispiel-Add-Ins für programmierte UI-Test für Excel)](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Sample Coded UI Test Extension for Excel (Beispielerweiterungen für programmierte UI-Test für Excel)](../test/sample-coded-ui-test-extension-for-excel.md)

