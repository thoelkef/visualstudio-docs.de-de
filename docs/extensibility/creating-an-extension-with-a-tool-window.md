---
title: Erstellen einer Erweiterung mit einem Toolfenster | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739539"
---
# <a name="create-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Werkzeugfenster

In diesem Verfahren erfahren Sie, wie Sie die VSIX-Projektvorlage und die **Elementvorlage für benutzerdefinierte seufzende Werkzeuge verwenden,** um eine Erweiterung mit einem Toolfenster zu erstellen.

## <a name="prerequisites"></a>Voraussetzungen

 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Erstellen eines Werkzeugfensters

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstWindow**. Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine Vorlagenvorlage für das Toolfenster mit dem Namen **MyWindow**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Benutzerdefiniertes Werkzeugfenster**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Dateinamen des Werkzeugfensters in *MyWindow.cs*.

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

   Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).

4. Wechseln Sie in der experimentellen Instanz zu**Andere Windows** **anzeigen** > .

   Sie sollten ein Menüelement für **MyWindow**sehen. Klicken Sie auf diese Schaltfläche.

   Sie sollten ein Tool-Fenster mit dem Titel **MyWindow** und einer Schaltfläche sehen, die **Click Me! sagt.**
