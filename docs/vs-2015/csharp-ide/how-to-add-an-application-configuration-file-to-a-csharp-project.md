---
title: 'Vorgehensweise: Hinzufügen einer Anwendungs Konfigurationsdatei zu einem c#-Projekt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667531"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Gewusst wie: Hinzufügen einer Anwendungskonfigurationsdatei zu einem C#-Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch Hinzufügen einer Anwendungskonfigurationsdatei (Datei „app.config“) zu einem C#-Projekt können Sie anpassen, wie die Common Language Runtime Assemblydateien sucht und lädt. Weitere Informationen zu Anwendungs Konfigurationsdateien finden Sie unter so sucht Common Language [Runtime](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)nach Assemblys.

> [!NOTE]
> Der Windows Store unterstützt nicht <xref:System.Configuration> . Daher enthalten Store-Apps keine app.config Vorlage.

 Bei der Projekterstellung kopiert die Entwicklungsumgebung automatisch die Datei app.config, ändert den Dateinamen der Kopie entsprechend Ihrer ausführbaren Datei und verschiebt die Kopie dann in das bin-Verzeichnis.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>So fügen Sie Ihrem c#-Projekt eine Anwendungs Konfigurationsdatei hinzu

1. Wählen Sie in der Menüleiste **Projekt**, **Neues Element hinzufügen**aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Erweitern Sie **installiert**, erweitern Sie **Visual c#-Elemente**, und wählen Sie dann die Vorlage **Anwendungs Konfigurationsdatei** aus.

3. Geben Sie im Textfeld **Name** einen Namen ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.

     Eine Datei mit dem Namen app.config wird Ihrem Projekt hinzugefügt.

## <a name="see-also"></a>Weitere Informationen
 [Verwalten von Anwendungseinstellungen (.net)](../ide/managing-application-settings-dotnet.md) [Konfigurationsdatei Schema](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [Konfigurieren von apps](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) Gewusst [wie: Konfigurieren einer APP für eine .NET Framework Version](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [mithilfe der Visual Studio-Entwicklungsumgebung für c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)