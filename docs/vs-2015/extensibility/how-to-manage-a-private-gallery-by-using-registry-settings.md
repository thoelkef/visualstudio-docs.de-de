---
title: 'Vorgehensweise: Verwalten eines privaten Katalogs mithilfe von Registrierungs Einstellungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204160"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Gewusst wie: Verwalten eines privaten Katalogs mithilfe von Registrierungseinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Administrator oder Entwickler einer isolierten Shellerweiterung sind, können Sie den Zugriff auf die Steuerelemente, Vorlagen und Tools in der Visual Studio Gallery, in der Beispiel Galerie oder in privaten Galerien steuern. Um einen Katalog verfügbar zu machen oder nicht verfügbar zu machen, erstellen Sie eine pkgdef-Datei, in der die geänderten Registrierungsschlüssel und deren Werte beschrieben werden.  
  
## <a name="managing-private-galleries"></a>Verwalten von privaten Galerien  
 Sie können eine pkgdef-Datei erstellen, um den Zugriff auf Galerien auf mehreren Computern zu steuern. Diese Datei muss das folgende Format aufweisen:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Der `Repositories` Schlüssel bezieht sich auf den Katalog, der aktiviert oder deaktiviert werden soll. Die Visual Studio Gallery und die Samples Gallery verwenden die folgenden Repository-GUIDs:  
  
- Visual Studio Gallery: 0F 45e408-7995-4375-9485-86b8db553dc9  
  
- Beispiel Katalog: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  Der `Disabled` Wert ist optional. Standardmäßig ist ein-Katalog aktiviert.  
  
  Der- `Priority` Wert bestimmt die Reihenfolge, in der die Galerien im Dialogfeld Optionen aufgelistet werden. Visual Studio Gallery hat Priorität 10, und die Samples Gallery hat Priorität 20. Private Galerien beginnen mit Priorität 100. Wenn mehrere Kataloge denselben Prioritätswert aufweisen, wird die Reihenfolge, in der Sie angezeigt werden, durch die Werte ihrer lokalisierten `DisplayName` Attribute bestimmt.  
  
  Der `Protocol` Wert ist für Atom-basierte oder SharePoint-basierte Galerien erforderlich.  
  
  Entweder `DisplayName` oder `DisplayNameResourceID` und `DisplayNamePackageGuid` müssen angegeben werden. Wenn all angegeben wird, wird das `DisplayNameResourceID` -Paar und das- `DisplayNamePackageGuid` Paar verwendet.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deaktivieren der Visual Studio Gallery mithilfe einer pkgdef-Datei  
 Sie können einen Katalog in einer pkgdef-Datei deaktivieren. Der folgende Eintrag deaktiviert die Visual Studio Gallery:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Der folgende Eintrag deaktiviert die Samples Gallery:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Private Kataloge](../extensibility/private-galleries.md)
