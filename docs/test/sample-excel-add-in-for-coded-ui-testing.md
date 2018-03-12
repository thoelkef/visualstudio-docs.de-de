---
title: "Beispiel-Excel-Add-In für Test der programmierten UI | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d6033b10ec7b8be4e44ad00c6f550d7237806234
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Sample Excel Add-In for Coded UI Testing
Dieses Beispiel-Add-In für [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] wurde speziell für die Unterstützung von Test der programmierten UI von Excel-Arbeitsblättern entworfen, die in Visual Studio Enterprise aufgezeichnet und ausgeführt werden. Das Add-In wird mit Visual Studio-Tools für Office erstellt.  
  
 Weitere Informationen über das Erstellen eines Excel-Add-Ins finden Sie unter [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f). Alternativ können Sie im MSDN nach „Excel-Add-In“ suchen.  
  
 Auch wenn es sich beim Excel-Add-In nicht um das Hauptthema dieser Dokumentation über die Erweiterung für Tests der programmierten UI für Excel handelt, sind einige Kommentare möglicherweise hilfreich.  
  
 Wichtige Teile dieses Add-Ins:  
  
-   `ThisAddIn`-Klasse: Verwaltet den .NET-Remotekanal zwischen `ExcelUICommunicator` und der [Beispielerweiterung für Tests der programmierten UI für Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`: Ein Sicherheitszertifikat zum Testen des Add-Ins.  
  
-   `ExcelUICommunicator`-Klasse: Diese Klasse implementiert die `IExcelUICommunication`-Schnittstelle.  
  
## <a name="thisaddin-class"></a>ThisAddIn-Klasse  
 Das Meiste dieser Klasse wird tatsächlich durch Visual Studio-Tools für Office in der `ThisAddIn.Designer.cs`-Datei generiert, wenn Sie Ihr Excel-Add-In-Projekt erstellen.  
  
 Bei den zu implementierenden Membern handelt es sich um die Ereignishandler `ThisAddIn_Startup()` und `ThisAddIn_Shutdown()`. Ihr Zweck besteht darin, den .NET-Remotekanal zu initialisieren oder zu schließen, der durch `ExcelUICommunicator` verwendet wird.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Diese Datei enthält ein temporäres Sicherheitszertifikat, das durch Visual Studio-Tools für Office generiert wird, und erteilt die Add-In-Assemblyberechtigung, um im Excel-Prozess den Test des Add-Ins und der Erweiterung verarbeiten zu können. Sie sollten dieses Zertifikat löschen und auf der Registerkarte **Signierung** des Projektfensters **Eigenschaften** ein neues erstellen oder Ihr eigenes Testzertifikat anfügen.  
  
## <a name="exceluicommunicator-class"></a>ExcelUICommunicator-Klasse  
 Diese Klasse implementiert die `IExcelUITestCommunication`-Schnittstelle und ruft die angeforderten Benutzeroberflächeninformationen aus dem Excel-Objektmodell ab. Weitere Informationen finden Sie unter [Beispiel für Excel-Communicator-Schnittstelle](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel (Erweitern von programmierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel)](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Office- und SharePoint-Entwicklung](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
