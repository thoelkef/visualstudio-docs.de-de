---
title: Erstellen Sie mit der Erweiterung Pack-Elementvorlage ein Erweiterungspaket | Microsoft-Dokumentation
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58193704"
---
# <a name="walkthrough-create-an-extension-pack"></a>Exemplarische Vorgehensweise: Erstellen eines Erweiterungspakets

Ein Erweiterungspaket ist ein Satz von Erweiterungen, die zusammen installiert werden können. Erweiterungsmodulen können Sie ganz einfach Ihre bevorzugten Erweiterungen für andere Benutzer freigeben oder einen Satz von Erweiterungen für ein bestimmtes Szenario zu bündeln.

## <a name="prerequisites"></a>Vorraussetzungen

Ab Visual Studio 2015 ist Visual Studio SDK als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Das Erweiterungspaket-Feature ist ab Visual Studio 15.8 Preview 2 verfügbar.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Erstellen Sie eine Erweiterung mit einer Elementvorlage-Erweiterungspaket

Die Elementvorlage-Erweiterungspaket erstellt ein Erweiterungspaket mit Satz von Erweiterungen, die zusammen installiert werden können.

1. In der **neues Projekt** Dialogfeld, und suchen Sie "Vsix", und wählen **VSIX-Projekt**. Für **Projektname**, geben Sie "Test-Erweiterungspaket". Wählen Sie **Erstellen** aus.

2. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Erweiterungspaket**. Lassen Sie den Standarddateinamen (ExtensionPack1.cs) aus.

3. ExtensionPack1.vsext-Datei hinzugefügt wird, die den folgenden Code enthält

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

4. Die Vsixid der Erweiterung der Erweiterungspaket einschließt finden Sie auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Suchen Sie nach der Erweiterung, die Sie einschließen möchten und klicken auf **Kopie-ID**. Aktualisieren Sie den vorhandenen **VsixId** in den oben genannten Datei oder eine andere Erweiterung der Liste hinzufügen.

    ![Kopieren Sie VsixId aus Marketplace](media/vsixid-marketplace.png)

5. Erstellen Sie das Projekt, und Laden Sie die Erweiterung im Marketplace hoch. Finden Sie unter [Veröffentlichung von Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Ein Erweiterungspaket kann nur installiert die Erweiterungen, die verfügbar sind die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder [privaten Katalog](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installieren Sie das Erweiterungspaket aus Visual Studio Marketplace

Nun, dass die Erweiterung veröffentlicht wurde, installieren Sie es in Visual Studio, und Testen sie dort.

::: moniker range="vs-2017"

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio auf die **Erweiterungen** Menü klicken Sie auf **Managed Extensions**.

::: moniker-end

2. Klicken Sie auf **Online** und suchen Sie nach "Test-Erweiterungspaket".

3. Klicken Sie auf **Download**. Die Erweiterung und die Liste der Erweiterungen in das Erweiterungspaket werden dann für die Installation geplant werden.

4. Im folgenden finden Sie eine Beispiel-Erweiterungspaket herunterladen Ansicht der **Verwalten von Erweiterungen** Dialogfeld. Wenn Sie nur einige der enthaltenen Erweiterungen in das Erweiterungspaket installieren möchten, können Sie ändern, dass die Liste der Erweiterungen in **installieren für geplante**.

    ![-Erweiterungspaket vom Marketplace herunterladen](media/vside-extensionpack.png)

5. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

So entfernen Sie die Erweiterung auf Ihrem Computer:

::: moniker range="vs-2017"

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio auf die **Erweiterungen** Menü klicken Sie auf **Managed Extensions**.

::: moniker-end

2. Wählen Sie **Test-Erweiterungspaket** , und klicken Sie dann auf **Deinstallieren**. Die Erweiterung und die Liste der Erweiterungen in das Erweiterungspaket werden dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
