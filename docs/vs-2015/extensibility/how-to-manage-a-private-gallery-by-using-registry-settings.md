---
title: 'Vorgehensweise: Verwalten eines privaten Katalogs mithilfe von Registrierungseinstellungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b65e4155cbe1a91836bf578fa6e60196f8f8579
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509914"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Vorgehensweise: Verwalten eines privaten Katalogs mithilfe von Registrierungseinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen](https://docs.microsoft.com/visualstudio/extensibility/how-to-manage-a-private-gallery-by-using-registry-settings).  
  
Wenn Sie ein Administrator oder Entwickler einer Isolated Shell-Erweiterung sind, können Sie den Zugriff auf den Steuerelementen, Vorlagen und Tools in Visual Studio Gallery, die Samples Gallery oder private Kataloge steuern. Um einen Katalog verfügbar oder nicht verfügbar machen, erstellen Sie eine PKGDEF-Datei, die die geänderte Registrierungsschlüssel und deren Werte beschreibt.  
  
## <a name="managing-private-galleries"></a>Verwalten von Private Kataloge  
 Sie können eine PKGDEF-Datei zum Steuern des Zugriffs für Kataloge auf mehreren Computern erstellen. Diese Datei muss das folgende Format haben.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Die `Repositories` Schlüssel verweist auf den Katalog aktiviert bzw. deaktiviert werden soll. Verwenden das folgende Repository GUIDs, die Visual Studio Gallery und die Samples Gallery:  
  
-   Visual Studio-Katalog: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Beispielkatalog: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 Die `Disabled` Wert ist optional. Standardmäßig wird ein Katalog aktiviert.  
  
 Die `Priority` Wert bestimmt die Reihenfolge, in der die Kataloge, klicken Sie im Dialogfeld Optionen aufgeführt sind. Visual Studio Gallery hat Priorität 10, und die Samples Gallery hat Priorität 20. Private Kataloge mit Priorität 100 beginnen. Wenn mehrere Kataloge denselben Prioritätswert aufweisen, ist die Reihenfolge, in der sie angezeigt werden, nach den Werten ihrer lokalisierten bestimmt `DisplayName` Attribute.  
  
 Die `Protocol` für Atom- oder SharePoint-basierten Katalogen ist erforderlich.  
  
 Entweder `DisplayName`, oder beides `DisplayNameResourceID` und `DisplayNamePackageGuid`, muss angegeben werden. Wenn all angegeben werden, und klicken Sie dann die `DisplayNameResourceID` und `DisplayNamePackageGuid` -Paar wird verwendet.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deaktivieren eine PKGDEF-Datei mit Visual Studio Gallery  
 Sie können einen Katalog im eine PKGDEF-Datei deaktivieren. Der folgende Eintrag wird der Visual Studio Gallery deaktiviert:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Der folgende Eintrag deaktiviert die Samples Gallery:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Private Kataloge](../extensibility/private-galleries.md)

