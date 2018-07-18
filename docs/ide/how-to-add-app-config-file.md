---
title: Vorgehensweise zum Hinzufügen einer Datei namens „app.config“ zu einem Projekt in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b2182b0175d57d7283e63bdf408249fa7566da00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31941973"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Vorgehensweise: Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

Durch Hinzufügen einer Anwendungskonfigurationsdatei (*app.config*) zu einem C#-Projekt können Sie anpassen, wie die Common Language Runtime Assemblydateien sucht und lädt. Weitere Informationen zu Anwendungskonfigurationsdateien finden Sie unter [So sucht die Common Language Runtime nach Assemblys (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> UWP-Apps enthalten keine Datei namens *app.config*.

Bei der Projekterstellung kopiert die Entwicklungsumgebung automatisch die Datei *app.config*, ändert den Dateinamen der Kopie entsprechend Ihrer ausführbaren Datei und verschiebt die Kopie dann in das **bin**-Verzeichnis.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Erweitern Sie **Installiert** > **Visual C#-Elemente**, und wählen Sie dann die Vorlage **Anwendungskonfigurationsdatei**.

1. Geben Sie im Textfeld **Name** einen Namen ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.

     Eine Datei namens *app.config* wird Ihrem Projekt hinzugefügt.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Anwendungseinstellungen (.NET)](../ide/managing-application-settings-dotnet.md)
- [Konfigurationsdateischema (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurieren von Apps (.NET Framework)](/dotnet/framework/configure-apps/index)