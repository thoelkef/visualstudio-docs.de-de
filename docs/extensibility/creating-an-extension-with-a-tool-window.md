---
title: Erstellen einer Erweiterung mit einem Toolfenster | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2741a7f9d27c303981ed4b179e3fe3d7cd63f020
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194148"
---
# <a name="create-an-extension-with-a-tool-window"></a>Erstellen Sie eine Erweiterung mit einem Toolfenster

In diesem Verfahren erfahren Sie, wie Sie die VSIX-Projektvorlage verwenden und die **benutzerdefinierten Toolfensters** Elementvorlage, die eine Erweiterung mit einem Toolfenster zu erstellen.

## <a name="prerequisites"></a>Vorraussetzungen

 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Erstellen eines Toolfensters

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstWindow**. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld, indem Sie nach "Vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage der Tool-Fenster mit dem Namen **MyWindow**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Toolfensters**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Dateinamen des Tool-Fenster an *MyWindow.cs*.

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

   Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

4. Wechseln Sie in der experimentellen Instanz zu **Ansicht** > **Other Windows**.

   Daraufhin sollte ein Menüelement für **MyWindow**. Klicken Sie darauf.

   Daraufhin sollte ein Toolfenster mit dem Titel **MyWindow** und einem Spruch Schaltfläche **hier klicken.**