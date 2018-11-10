---
title: Hinzufügen von Azure Storage mithilfe von verbundenen Diensten in Visual Studio | Microsoft-Dokumentation
description: Hinzufügen von Azure Storage zu Ihrer app mithilfe der im Dialogfeld "Visual Studio verbundene Dienste hinzufügen"
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001703"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Hinzufügen von Azure Storage mithilfe von Visual Studio verbundene Dienste
Mit Visual Studio, Sie können eine der folgenden mit Azure Storage Verbinden mit der **verbundene Dienste hinzufügen** Dialogfeld:

- C#Cloud-Dienst
- Mobilen .NET Back-End-Dienst
- ASP.NET-Website oder Dienst
- ASP.NET Core-Dienst
- Azure WebJob-Dienst 

Die Funktion für verbundene Dienste, die benötigten Verweise und der Verbindungscode zu Ihrem Projekt hinzugefügt, und Ihre Konfigurationsdateien entsprechend geändert. 

Nach Abschluss des Vorgangs die **verbundene Dienste hinzufügen** Dialogfeld automatisch zeigt die Dokumentation, die über die erforderlichen Schritte zum Arbeiten mit Blob Storage-Warteschlangen und Tabellen.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Verbinden Sie mit Azure Storage über das Dialogfeld "verbundene Dienste"
1. Öffnen Sie Ihr Projekt in Visual Studio

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **verbundene Dienste** Knoten aus dem Kontextmenü, und wählen **verbundenen Dienst hinzufügen**.
   
    ![Fügen Sie Azure verbundener Dienst](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. In der **verbundene Dienste** Seite **Cloudspeicher mit Azure Storage**.
   
    ![Azure Storage hinzufügen](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. In der **Azure Storage** Dialogfeld, wählen Sie ein vorhandenes Speicherkonto, und wählen **hinzufügen**.
   
    Wenn Sie ein Speicherkonto erstellen möchten, wechseln Sie mit dem nächsten Schritt. Fahren Sie andernfalls mit Schritt 6 fort.
    
    ![Vorhandenes Speicherkonto zum Projekt hinzufügen](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. So erstellen Sie ein Storage-Konto: 
   
   1. Wählen Sie **Erstellen eines neuen Speicherkontos** am unteren Rand des Dialogfelds.

   1. Füllen Sie die **Create Storage Account** Dialogfeld ein, und wählen Sie **erstellen**.
      
       ![Neues Azure Storage-Konto](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. Wenn die **Azure Storage** Dialogfeld wird angezeigt, das neue Speicherkonto in der Liste angezeigt. Wählen Sie das neue Speicherkonto in der Liste aus, und wählen **hinzufügen**.

1. Der Speicher verbundener Dienst unter wird der **Dienstverweise** Knoten des Projekts.
   
## <a name="how-your-project-is-modified"></a>Erläutert, wie Ihr Projekt ändern
Wenn Sie das Dialogfeld abgeschlossen haben, wird Visual Studio fügt Verweise hinzu und ändert bestimmte Konfigurationsdateien. Die genauen Änderungen hängen vom Projekttyp ab: 

- ASP.NET-Projekt – [Was ist passiert – ASP.NET-Projekte](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core-Projekt - [Was ist passiert – ASP.NET 5-Projekte](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- Clouddienstprojekt (Web- und Workerrollen) - [Was ist passiert – clouddienstprojekte](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob-Projekt: [Was ist passiert – WebJob-Projekte](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Nächste Schritte
- [MSDN-Forum: Azure-Speicher](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure Storage-Teamblog](http://blogs.msdn.com/b/windowsazurestorage/)
- [Azure Storage-Dokumentation](https://docs.microsoft.com/azure/storage/)
