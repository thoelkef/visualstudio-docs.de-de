---
title: Private Kataloge | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: e4c49a19a9befad5d90b9526842786f49af0851b
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="private-galleries"></a>Private Galleries
Sie können den Steuerelementen, Vorlagen und Tools, die Sie entwickeln, indem sie auf bereitgestellt Freigeben einer *privaten Katalog* im Intranet Ihres Unternehmens wie folgt:  
  
-   Erstellen Sie einen Atom (RSS)-feed entsprechend konfigurierten zentral (Repository) in Ihrem Intranet. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Atom-Feed für einen privaten Katalog](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Verteilen Sie eine PKGDEF-Datei, die den privaten Katalog beschreibt. Es wird empfohlen, diese Konfiguration für Administratoren, die einen privaten Katalog auf mehreren Computern gleichzeitig eine Verbindung herstellen möchten.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Hinzufügen von privaten Katalog mit den Erweiterungen und Updates in Visual Studio  
 Wenn Sie ein privater Katalog verfügbar ist, können Sie ihn zum Hinzufügen **Erweiterungen und Updates** in Visual Studio.  
  
 ![Dialogfeld "hinzufügen" Erweiterungs-Manager](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>So fügen Sie einen privaten Katalog mit den Erweiterungen und Updates hinzu  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  In der **Umgebung** Knoten **Erweiterungen und Updates**.  
  
3.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
4.  In der **Namen** Feld, z. B. Geben Sie einen Namen für den privaten Katalog `My Gallery`.  
  
5.  In der **URL** Feld, geben Sie die URL des Atom-feed oder SharePoint-Website, die den privaten Katalog hostet.  
  
    1.  Wenn ein Atom-feed handelt, mit dem privaten Katalog verbunden wird, ähnelt die URL dieser: http://www.mywebsite/mygallery/atom.xml.  Diese URL kann auf eine Datei oder ein Netzwerkpfad verweisen.  
  
    2.  Wenn der Host einer SharePoint-Website befindet, die URL ähnelt dieser: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Verwalten von Private Kataloge  
 Ein Administrator kann einen privaten Katalog auf mehreren Computern gleichzeitig zur Verfügung durch Ändern der Registrierungs auf jedem Computer. Um dies zu erreichen, erstellen Sie eine PKGDEF-Datei, die die neuen Registrierungsschlüssel und ihre Werte beschreibt.  Das Format dieser Datei lautet wie folgt.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten einer privaten Katalog von mithilfe von Registry Settings](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Installieren von Erweiterungen von privaten Katalog  
 Sie können Suchen und installieren Sie Visual Studio-Erweiterungen aus einem privaten Katalog in **Erweiterungen und Updates**. Die folgenden Schritte verwenden, einen privaten Katalog mit dem Namen `My Gallery`.  
  
 ![Erweiterungs-Manager installieren der privaten Galerie](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Suchen und Installieren von Erweiterungen aus einem privaten Katalog  
  
1.  Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2.  Wählen Sie im linken Bereich **Onlineerweiterungen**, und wählen Sie dann **Meine Katalog**.  
  
3.  Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **herunterladen** Schaltfläche.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Aktualisieren von Erweiterungen von einem der privaten Galerie  
 Wenn neue Versionen von Visual Studio-Erweiterungen in der privaten Galerie gesendet werden, können die Erweiterungen aktualisiert werden, die Sie installiert haben. Die folgenden Schritte verwenden, einen privaten Katalog mit dem Namen `My Repository`.  
  
 ![Erweiterungs-Manager-Katalog Aktualisierung der privaten](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Beim Aktualisieren einer installierten-Erweiterungs aus einem privaten Katalog  
  
1.  Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2.  Wählen Sie im linken Bereich **Updates**, und wählen Sie dann **Meine Repository**.  
  
3.  Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **Update** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)   
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
