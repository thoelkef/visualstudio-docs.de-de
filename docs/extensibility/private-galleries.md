---
title: Private Kataloge | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027181d16024964d5487be2b3eb0b4ca261f98e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079226"
---
# <a name="private-galleries"></a>Private Kataloge
Sie können die Steuerelemente, Vorlagen und Tools, die Sie entwickeln, indem Sie sie veröffentlichen Freigeben einer *privaten Katalog* im Intranet für Ihre Organisation wie folgt:

- Erstellen Sie ein Atom (RSS-Feeds) entsprechend konfigurierten zentral (Repository) in Ihrem Intranet. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie einen Atom-feed für einen privaten Katalog](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Verteilen einer *PKGDEF* Datei, die den privaten Katalog beschreibt. Es wird empfohlen, diese Konfiguration für Administratoren, die einen privaten Katalog auf mehreren Computern gleichzeitig eine Verbindung herstellen möchten.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Fügen Sie einen privaten Katalog mit den Erweiterungen und Updates in Visual Studio
 Wenn Sie ein privater Katalog verfügbar ist, können Sie ihn zum Hinzufügen **Erweiterungen und Updates** in Visual Studio.

 ![Dialogfeld "Erweiterungs-Manager hinzufügen"](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Um einen privaten Katalog mit den Erweiterungen und Updates hinzuzufügen

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

2. In der **Umgebung** Knoten **Erweiterungen und Updates**.

3. Wählen Sie die Schaltfläche **Hinzufügen** aus.

4. In der **Namen** Geben Sie einen Namen für den privaten Katalog, z. B. `My Gallery`.

5. In der **URL** Geben Sie die URL des Atom-feed oder SharePoint-Website, die den privaten Katalog hostet.

    1. Wenn der Host ein Atom-feed ist, die eine Verbindung mit dem privaten Katalog her, die URL ähnelt dieser: http://www.mywebsite/mygallery/atom.xml.  Diese URL kann auf eine Datei oder einen Netzwerkpfad verweisen.

    2. Wenn der Host auf einer SharePoint-Website ist, die URL ähnelt dieser: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.

### <a name="manage-private-galleries"></a>Verwalten Sie private Kataloge
 Ein Administrator kann einen privaten Katalog auf mehreren Computern gleichzeitig zur Verfügung durch Ändern der Registrierungs des Systems auf jedem Computer. Um dies zu erreichen, erstellen Sie eine *PKGDEF* -Datei, die die neuen Registrierungsschlüssel und ihre Werte beschreibt.  Das Format dieser Datei lautet wie folgt aus.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten ein privates Katalogs mithilfe von registrierungseinstellungen](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installieren von Erweiterungen über einen privaten Katalog
 Sie können nach suchen und installieren Sie Visual Studio-Erweiterungen über einen privaten Katalog in **Erweiterungen und Updates**. Die folgenden Schritte verwenden, einen privaten Katalog mit dem Namen `My Gallery`.

 ![Erweiterungs-Manager, die Installation von privaten Katalog](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Suchen und Installieren von Erweiterungen über einen privaten Katalog

1. Wählen Sie auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

2. Wählen Sie im linken Bereich **Onlineerweiterungen**, und wählen Sie dann **Meine Galerie**.

3. Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **herunterladen** Schaltfläche.

## <a name="update-extensions-from-a-private-gallery"></a>Aktualisieren von Erweiterungen, die über einen privaten Katalog
 Neue Versionen von Visual Studio-Erweiterungen in den privaten Katalog bereitgestellt werden, können Sie die Erweiterungen aktualisieren, die Sie installiert haben. Die folgenden Schritte verwenden, einen privaten Katalog mit dem Namen `My Repository`.

 ![Aktualisierung der Erweiterung Manager privaten Galerie](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Um eine installierte Erweiterung mithilfe eines privaten Katalogs zu aktualisieren.

1. Wählen Sie auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

2. Wählen Sie im linken Bereich **Updates**, und wählen Sie dann **mein Repository**.

3. Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **Update** Schaltfläche.

## <a name="see-also"></a>Siehe auch
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
- [Senden von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)