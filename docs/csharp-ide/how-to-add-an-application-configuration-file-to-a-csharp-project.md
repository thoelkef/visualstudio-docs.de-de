---
title: "Vorgehensweise: hinzufügen eine Anwendungskonfigurationsdatei zu einem c#-Projekt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 707100d33e91d1b0920d008140dc2fb6f1e078fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Gewusst wie: Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt
Ein C#-Projekt eine Anwendungskonfigurationsdatei (app.config-Datei) hinzufügen, können Sie anpassen, wie die common Language Runtime sucht und lädt die Assemblydateien. Weitere Informationen über Anwendungskonfigurationsdateien finden Sie unter [so sucht Common Language Runtime nach Assemblys](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Uwp-apps nicht auf eine Vorlage für "App.config" enthalten.
  
 Wenn Sie das Projekt erstellen, die Entwicklungsumgebung automatisch kopiert die Datei "App.config" ändert sich der Dateiname des Kopiervorgangs entsprechend Ihrer ausführbaren Datei und anschließend wird die Kopie in das Verzeichnis "bin" verschoben.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Das C#-Projekt eine Anwendungskonfigurationsdatei hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Erweitern Sie **installiert**, erweitern Sie **Visual C#-Elemente**, und wählen Sie dann die **Anwendungskonfigurationsdatei** Vorlage.  
  
3.  In der **Namen** Textfeld, geben Sie einen Namen, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Eine Datei mit dem Namen "App.config" wird dem Projekt hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Anwendungseinstellungen (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Konfigurationsdateischema](/dotnet/framework/configure-apps/file-schema/index)   
 [Konfigurieren von Apps](/dotnet/framework/configure-apps/index)   
 [Vorgehensweise: Konfigurieren Sie eine Anwendung, um eine .NET Framework-Version als Ziel](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Verwenden der Visual Studio-Entwicklungsumgebung für C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)