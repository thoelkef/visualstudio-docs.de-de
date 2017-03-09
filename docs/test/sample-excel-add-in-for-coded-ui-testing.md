---
title: "Sample Excel Add-In for Coded UI Testing | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tests für codierte UI, Excel-Add-In (Beispiel)"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Sample Excel Add-In for Coded UI Testing
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Beispiel\-Add\-In für [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] wurde speziell für die Unterstützung von Test der programmierten UI von Excel\-Arbeitsblättern entworfen, die in Visual Studio Enterprise aufgezeichnet und ausgeführt werden. Das Add\-In wird mit Visual Studio\-Tools für Office erstellt.  
  
 Weitere Informationen über das Erstellen eines Excel\-Add\-Ins finden Sie unter [Exemplarische Vorgehensweise: Erstellen des ersten VSTO\-Add\-Ins für Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md). Alternativ können Sie im MSDN nach „Excel\-Add\-In“ suchen.  
  
 Auch wenn es sich beim Excel\-Add\-In nicht um das Hauptthema dieser Dokumentation über die Erweiterung für Tests der programmierten UI für Excel handelt, sind einige Kommentare möglicherweise hilfreich.  
  
 Wichtige Teile dieses Add\-Ins:  
  
-   `ThisAddIn` \-Class: Verwaltet den .NET\-Remotekanal zwischen `ExcelUICommunicator` und der [Sample Coded UI Test Extension for Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` : Ein Sicherheitszertifikat zum Testen des Add\-Ins.  
  
-   `ExcelUICommunicator` \-Klasse: Diese Klasse implementiert die `IExcelUICommunication`\-Schnittstelle.  
  
## ThisAddIn\-Klasse  
 Das Meiste dieser Klasse wird tatsächlich durch Visual Studio\-Tools für Office in der `ThisAddIn.Designer.cs`\-Datei generiert, wenn Sie Ihr Excel\-Add\-In\-Projekt erstellen.  
  
 Bei den zu implementierenden Membern handelt es sich um die Ereignishandler `ThisAddIn_Startup()` und `ThisAddIn_Shutdown()`.  Ihr Zweck besteht darin, den .NET\-Remotekanal zu initialisieren oder zu schließen, der durch `ExcelUICommunicator` verwendet wird.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Diese Datei enthält ein temporäres Sicherheitszertifikat, das durch Visual Studio\-Tools für Office generiert wird, und erteilt die Add\-In\-Assemblyberechtigung, um im Excel\-Prozess den Test des Add\-Ins und der Erweiterung verarbeiten zu können.  Sie sollten dieses Zertifikat löschen und auf der Registerkarte **Signierung** des Projektfensters **Eigenschaften** ein neues erstellen oder Ihr eigenes Testzertifikat anfügen.  
  
## ExcelUICommunicator\-Klasse  
 Diese Klasse implementiert die `IExcelUITestCommunication`\-Schnittstelle und ruft die angeforderten Benutzeroberflächeninformationen aus dem Excel\-Objektmodell ab.  Weitere Informationen finden Sie unter [Beispiel für Excel\-Communicator\-Schnittstelle](../test/sample-excel-communicator-interface.md).  
  
## Siehe auch  
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO\-Add\-Ins für Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)