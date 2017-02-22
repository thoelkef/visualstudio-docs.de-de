---
title: "Beispiel f&#252;r Excel-Communicator-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Beispiel f&#252;r Excel-Communicator-Schnittstelle
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Beispielschnittstelle für `IExcelUICommunication` wird im `ExcelUICommunicator`\-Objekt im `ExcelAddIn`\-Projekt verwendet.  
  
## IExcelUICommunications\-Schnittstelle  
 Diese Schnittstelle definiert die Kommunikationspunkte zwischen dem `CodedUIExtension`\-Objekt, das im Prozess des Tests der codierten UI ausgeführt wird, und dem `ExcelCodedUIAddIn`\-Objekt, das im [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]\-Prozess ausgeführt wird.  
  
 Die `ExcelCodedUIAddinHelper`\-Assembly verfügt über eine `ExcelUICommunicator`\-Klasse, die von dieser Schnittstelle abgeleitet ist und das Excel\-Objektmodell zum Verarbeiten der Methoden verwendet.  
  
 Einige Methoden rufen die angeforderten Informationen von Excel ab und erstellen dann eines der Informationsobjekte und geben es zurück, z. B. das `CellInformation`\-Objekt.  
  
 Andere Methoden verwenden ein bereitgestelltes Informationsobjekt, suchen das entsprechende Steuerelement in Excel und führen einen Prozess für das Steuerelement aus.  Die `ScrollIntoView`\-Methode führt z. B. einen Bildlauf im Arbeitsblatt durch, damit die festgelegte Zelle sichtbar ist.  
  
## Kommunikation von CodedUIExtensibilitySample und ExcelCodedUIAddinHelper  
 Die `ExcelCodedUIAddinHelper`\-Assembly wird im Excel\-Prozess ausgeführt und verfügt über die `UICommunicator`\-Klasse, die die `IExcelUITestCommunication`\-Schnittstelle implementiert und die erforderlichen Informationen direkt von der Excel\-Benutzeroberfläche abruft oder festlegt.  
  
 Die `CodedUIExtensibilitySample`\-Assembly wird im Prozess des Tests der codierten UI von Visual Studio ausgeführt.  Diese Assembly verfügt über die `Communicator`\-Klasse, die einen .NET\-Remotingchannel öffnet, und stellt eine `Instance`\-Eigenschaft bereit, die mithilfe der `IExcelUICommunication`\-Schnittstelle das `UICommunicator`\-Objekt in der `ExcelCodedUIAddinHelper`\-Assembly verwendet, um Anforderungen und Informationsobjekte zwischen den beiden Assemblys zu übergeben, z. B. ein `CellInformation`\-Objekt.  
  
## Siehe auch  
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Sample Excel Add\-In for Coded UI Testing](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Sample Coded UI Test Extension for Excel](../test/sample-coded-ui-test-extension-for-excel.md)