---
title: Erstellen eines Erweiterungspakets
description: Erfahren Sie, wie Sie mit der Element Vorlage für das Erweiterungspaket ein Erweiterungspaket erstellen.
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: b5a0021061aefceafc2b048a3e231d9c0300db7b
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742917"
---
# <a name="walkthrough-create-an-extension-pack"></a>Exemplarische Vorgehensweise: Erstellen eines Erweiterungspakets

Ein Erweiterungspaket ist ein Satz von Erweiterungen, die gleichzeitig installiert werden können. Mithilfe von Erweiterungs Paketen können Sie Ihre bevorzugten Erweiterungen problemlos für andere Benutzer freigeben oder einen Satz von Erweiterungen für ein bestimmtes Szenario zusammenfassen.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 ist das Visual Studio SDK als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Das Erweiterungspaket Feature ist ab Visual Studio 15,8 Preview 2 verfügbar.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Erstellen einer Erweiterung mit einer Element Vorlage für das Erweiterungspaket

Mit der Element Vorlage für das Erweiterungspaket wird ein Erweiterungspaket mit einer Reihe von Erweiterungen erstellt, die gleichzeitig installiert werden können.

1. Suchen Sie im Dialogfeld **Neues Projekt** nach "VSIX", und wählen Sie **VSIX-Projekt**aus. Geben Sie unter **Projektname den Namen**"Test Extension Pack" ein. Klicken Sie auf **Erstellen**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Add**  >  **Neues Element**hinzufügen aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Erweiterungspaket**aus. Belassen Sie den Standard Dateinamen (ExtensionPack1.cs).

3. Die Datei "ExtensionPack1. VSExt" wurde hinzugefügt, die den folgenden Code enthält:

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Die vsixid der in das Erweiterungspaket einzuschließenden Erweiterung finden Sie auf der [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Suchen Sie die Erweiterung, die Sie einschließen möchten, und klicken Sie auf die **Kopier-ID**. Sie können die vorhandene **vsixid** in der obigen Datei aktualisieren oder eine weitere Erweiterung zur Liste hinzufügen.

    ![Vsixid aus Marketplace kopieren](media/vsixid-marketplace.png)

5. Erstellen Sie das Projekt, und laden Sie die Erweiterung in den Marketplace hoch. Weitere Informationen finden Sie unter [Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Mit einem Erweiterungspaket können nur Erweiterungen installiert werden, die im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder im [privaten](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)Katalog verfügbar sind.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installieren Sie das Erweiterungspaket aus dem Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie Sie in Visual Studio und testen Sie dort.

::: moniker range="vs-2017"

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie in Visual Studio im Menü **Erweiterungen** auf **verwaltete Erweiterungen**.

::: moniker-end

2. Klicken Sie auf **Online** , und suchen Sie nach "Test Extension Pack".

3. Klicken Sie auf **Download**. Die Erweiterung und die Liste der Erweiterungen, die im Erweiterungspaket enthalten sind, werden dann für die Installation geplant.

4. Im folgenden finden Sie eine Beispiel-Erweiterungspaket-Download Ansicht des Dialog Felds **Erweiterungen verwalten** . Wenn Sie es vorziehen, nur einige der enthaltenen Erweiterungen im Erweiterungspaket zu installieren, können Sie die Erweiterungs Liste in " **geplant für die Installation**" ändern.

    ![Erweiterungspaket vom Marketplace herunterladen](media/vside-extensionpack.png)

5. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

So entfernen Sie die Erweiterung auf dem Computer:

::: moniker range="vs-2017"

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie in Visual Studio im Menü **Erweiterungen** auf **verwaltete Erweiterungen**.

::: moniker-end

2. Wählen Sie **Test Erweiterungspaket** aus, und klicken Sie auf **deinstallieren**. Die Erweiterung und die Liste der Erweiterungen, die im Erweiterungspaket enthalten sind, werden dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.
