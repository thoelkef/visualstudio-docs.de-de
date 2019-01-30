---
title: So fügen Sie einem Projekt die Datei „app.config“ hinzu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4c34a0d8f2a04718ff409ed5256eea1c07287f95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992476"
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