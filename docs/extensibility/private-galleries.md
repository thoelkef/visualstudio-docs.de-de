---
title: "Private Galerien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Private VSIX Galerien"
  - "Private Galerien VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Private Galerien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Steuerelemente, Vorlagen und Tools, die Sie entwickeln, veröffentlichen Sie sie freigeben einer *private Galerie* im Intranet Ihres Unternehmens wie folgt:  
  
-   Erstellen Sie ein Atom \(RSS\-Feeds\) entsprechend konfigurierten zentral \(Repository\) in Ihrem Intranet. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen Sie einen Atom\-Feed für einen privaten Galerie](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Verteilen Sie eine PKGDEF\-Datei, die den privaten Katalog beschreibt. Es wird empfohlen, diese Konfiguration für Administratoren, die eine private Galerie zu viele Computer gleichzeitig eine Verbindung herstellen möchten.  
  
## Hinzufügen einer privaten Galerie Erweiterungen und Updates in Visual Studio  
 Wenn eine private Galerie verfügbar ist, fügen Sie ihn können **Erweiterungen und Updates** in Visual Studio.  
  
 ![Erweiterungs&#45;Manager – Dialogfeld „Hinzufügen“](~/docs/extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### Um eine private Galerie Erweiterungen und Updates hinzufügen  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  In der **Umgebung** Knoten **Erweiterungen und Updates**.  
  
3.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
4.  In den **Namen** Geben Sie einen Namen für die private Galerie, z. B. `My Gallery`.  
  
5.  In der **URL** Geben Sie die URL der SharePoint\-Website, die den privaten Katalog hostet oder Atom\-feed.  
  
    1.  Wenn ein Atom\-feed handelt, die mit dem privaten Katalog verbunden, ähnelt die URL dieser: http:\/\/www.mywebsite\/mygallery\/atom.xml.  Diese URL kann auf eine Datei oder einen Netzwerkpfad verweisen.  
  
    2.  Wenn der Host einer SharePoint\-Website ist, würde die URL ähneln dieser: http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx.  
  
### Verwalten von privaten Galerien  
 Ein Administrator kann eine private Galerie auf mehreren Computern gleichzeitig zur Verfügung durch Ändern der Registrierungs auf jedem Computer. Um dies zu erreichen, erstellen Sie eine PKGDEF\-Datei, die die neuen Registrierungsschlüssel und ihre Werte beschreibt.  Das Format dieser Datei lautet wie folgt.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## Installieren von Erweiterungen in einer privaten Galerie  
 Sie können Suchen und Installieren von Visual Studio\-Erweiterungen aus einem privaten Katalog in **Erweiterungen und Updates**. Mithilfe der folgenden Schritte eine private Galerie mit dem Namen `My Gallery`.  
  
 ![Erweiterungs&#45;Manager – Installieren der privaten Galerie](~/docs/extensibility/media/em_.png "EM\_")  
  
#### Suchen und installieren Sie Erweiterungen aus einer privaten Galerie  
  
1.  Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2.  Wählen Sie im linken Bereich **Onlineerweiterungen**, und wählen Sie dann **Meine Galerie**.  
  
3.  Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **herunterladen** Schaltfläche.  
  
## Aktualisieren von Erweiterungen in einer privaten Galerie  
 Wenn neue Versionen von Visual Studio\-Erweiterungen in der privaten Galerie bereitgestellt werden, können Sie die Erweiterungen aktualisieren, die Sie installiert haben. Mithilfe der folgenden Schritte eine private Galerie mit dem Namen `My Repository`.  
  
 ![Erweiterungs&#45;Manager – Aktualisierung der privaten Galerie](~/docs/extensibility/media/em_update.png "EM\_Update")  
  
#### Eine installierte Erweiterung aus einem privaten Katalog aktualisieren  
  
1.  Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2.  Wählen Sie im linken Bereich **Updates**, und wählen Sie dann **Mein Repository**.  
  
3.  Wählen Sie im rechten Bereich eine Erweiterung, und wählen Sie dann die **Update** Schaltfläche.  
  
## Siehe auch  
 [Suchen und Verwenden von Visual Studio\-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)   
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)