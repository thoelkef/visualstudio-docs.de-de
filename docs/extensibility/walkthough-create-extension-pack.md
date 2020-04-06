---
title: Erstellen eines Erweiterungspakets mit der Erweiterungspaket-Elementvorlage | Microsoft Docs
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
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697750"
---
# <a name="walkthrough-create-an-extension-pack"></a>Exemplarische Vorgehensweise: Erstellen eines Erweiterungspakets

Ein Extension Pack ist ein Satz von Erweiterungen, die zusammen installiert werden können. Mit Extension Packs können Sie Ihre bevorzugten Erweiterungen ganz einfach mit anderen Benutzern teilen oder eine Reihe von Erweiterungen für ein bestimmtes Szenario bündeln.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 ist das Visual Studio SDK als optionale Funktion in Visual Studio-Setup eingeschlossen. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Die Erweiterungspaketfunktion ist ab Visual Studio 15.8 Preview 2 verfügbar.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Erstellen einer Erweiterung mit einer Extension Pack-Elementvorlage

Die Erweiterungspaket-Elementvorlage erstellt ein Extension Pack mit Erweiterungen, die zusammen installiert werden können.

1. Suchen Sie im Dialogfeld **Neues Projekt** nach "vsix" und wählen Sie **VSIX Project**aus. Geben Sie für **Project name**"Test Extension Pack" ein. Klicken Sie auf **Erstellen**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie zum Visual **C-Extensibility-Knoten,** und wählen Sie **Extension Pack**aus. Lassen Sie den Standarddateinamen (ExtensionPack1.cs).

3. ExtensionPack1.vsext Datei hinzugefügt, die den folgenden Code enthält

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

4. Die vsixid der Erweiterung, die in das Extension Pack aufgenommen werden soll, finden Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Suchen Sie die Erweiterung, die Sie einschließen möchten, und klicken Sie auf **Kopier-ID**. Sie können die vorhandene **vsixId** in der obigen Datei aktualisieren oder der Liste eine weitere Erweiterung hinzufügen.

    ![VsixId aus dem Marketplace kopieren](media/vsixid-marketplace.png)

5. Erstellen Sie das Projekt und laden Sie Ihre Erweiterung in den Marketplace hoch. Weitere Informationen finden Sie unter [Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Ein Erweiterungspaket kann nur Erweiterungen installieren, die im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder in der Privaten [Galerie](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)verfügbar sind.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installieren des Extension Packs aus dem Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie sie in Visual Studio und testen Sie sie dort.

::: moniker range="vs-2017"

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie in Visual Studio im Menü **Erweiterungen** auf **Verwaltete Erweiterungen**.

::: moniker-end

2. Klicken Sie auf **Online** und suchen Sie dann nach "Test Extension Pack".

3. Klicken Sie auf **Download**. Die Erweiterung und die Liste der erweiterungen, die im Extension Pack enthalten sind, werden dann für die Installation geplant.

4. Unten finden Sie eine Beispielansicht zum Erweiterungspaket im Dialogfeld **Erweiterungen verwalten.** Wenn Sie nur einige der im Erweiterungspaket enthaltenen Erweiterungen installieren möchten, können Sie die Erweiterungsliste in **Scheduled For Install**ändern.

    ![Extension Pack von Marketplace herunterladen](media/vside-extensionpack.png)

5. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

So entfernen Sie die Erweiterung von Ihrem Computer:

::: moniker range="vs-2017"

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie in Visual Studio im Menü **Erweiterungen** auf **Verwaltete Erweiterungen**.

::: moniker-end

2. Wählen Test **Extension Pack** und dann auf **Deinstallieren**. Die Erweiterung und die Liste der erweiterungen, die im Extension Pack enthalten sind, werden dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
