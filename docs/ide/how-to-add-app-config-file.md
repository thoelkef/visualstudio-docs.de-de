---
title: "Vorgehensweise zum Hinzufügen einer Datei namens „app.config“ zu einem Projekt in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Gewusst wie: Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

Durch Hinzufügen einer Anwendungskonfigurationsdatei (Datei „app.config“) zu einem C#-Projekt können Sie anpassen, wie die Common Language Runtime Assemblydateien sucht und lädt. Weitere Informationen zu Anwendungskonfigurationsdateien finden Sie unter [Vorgehensweise zum Suchen der Common Language Runtime nach Assemblys (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> UWP-Apps enthalten keine Datei namens „app.config“.

Bei der Projekterstellung kopiert die Entwicklungsumgebung automatisch die Datei „app.config“, ändert den Dateinamen der Kopie entsprechend Ihrer ausführbaren Datei und verschiebt die Kopie dann in das **bin**-Verzeichnis.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Erweitern Sie **Installiert** > **Visual C#-Elemente**, und wählen Sie dann die Vorlage **Anwendungskonfigurationsdatei**.

3. Geben Sie im Textfeld **Name** einen Namen ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.

     A file named app.config is added to your project.

## <a name="see-also"></a>Siehe auch

[Verwalten von Anwendungseinstellungen (.NET)](../ide/managing-application-settings-dotnet.md)  
[Konfigurationsdateischema (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Konfigurieren von Apps (.NET Framework)](/dotnet/framework/configure-apps/index)