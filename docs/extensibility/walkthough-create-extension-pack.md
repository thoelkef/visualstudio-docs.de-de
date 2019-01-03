---
title: Erstellen Sie mit der Erweiterung Pack-Elementvorlage ein Erweiterungspaket | Microsoft-Dokumentation
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 55ceb788807f5d4fc9de2a96b4d359f290218dda
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866321"
---
# <a name="walkthrough-create-an-extension-pack"></a>Exemplarische Vorgehensweise: Erstellen Sie ein Erweiterungspaket

Ein Erweiterungspaket ist ein Satz von Erweiterungen, die zusammen installiert werden können. Erweiterungsmodulen können Sie ganz einfach Ihre bevorzugten Erweiterungen für andere Benutzer freigeben oder einen Satz von Erweiterungen für ein bestimmtes Szenario zu bündeln.
  
## <a name="prerequisites"></a>Vorraussetzungen

Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

Das Erweiterungspaket-Feature ist ab Visual Studio 15.8 Preview 2 verfügbar.
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Erstellen Sie eine Erweiterung mit einer Elementvorlage-Erweiterungspaket

Die Elementvorlage-Erweiterungspaket erstellt ein Erweiterungspaket mit Satz von Erweiterungen, die zusammen installiert werden können.
  
1. In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** wählen Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `Test Extension Pack`ein. Klicken Sie auf **OK**.  
  
2. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Erweiterungspaket**. Lassen Sie den Standarddateinamen (ExtensionPack1.cs) aus.  
  
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

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates...** .

2. Klicken Sie auf **Online** und suchen Sie nach `Test Extension Pack`.

3. Klicken Sie auf **Download**. Die Erweiterung und die Liste der Erweiterungen in das Erweiterungspaket werden dann für die Installation geplant werden.

4. Im folgenden finden Sie eine Beispiel-Erweiterungspaket herunterladen Ansicht der **Erweiterungen und Updates** Dialogfeld. Wenn Sie nur einige der enthaltenen Erweiterungen in das Erweiterungspaket installieren möchten, können Sie ändern, dass die Liste der Erweiterungen in **installieren für geplante**.

    ![-Erweiterungspaket vom Marketplace herunterladen](media/vside-extensionpack.png)

5. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

So entfernen Sie die Erweiterung auf Ihrem Computer:

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates...** .

2. Wählen Sie `Test Extension Pack` , und klicken Sie dann auf **Deinstallieren**. Die Erweiterung und die Liste der Erweiterungen in das Erweiterungspaket werden dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
