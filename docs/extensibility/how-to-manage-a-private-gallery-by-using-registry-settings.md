---
title: 'Gewusst wie: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710933"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Gewusst wie: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen
Wenn Sie Administrator oder Entwickler einer isolierten Shell-Erweiterung sind, können Sie den Zugriff auf die Steuerelemente, Vorlagen und Tools in der Visual Studio-Galerie, im Beispielkatalog oder in privaten Galerien steuern. Um einen Katalog verfügbar oder nicht verfügbar zu machen, erstellen Sie eine *.pkgdef-Datei,* die die geänderten Registrierungsschlüssel und ihre Werte beschreibt.

## <a name="manage-private-galleries"></a>Verwalten privater Galerien
 Sie können eine *.pkgdef-Datei* erstellen, um den Zugriff auf Galerien auf mehreren Computern zu steuern. Diese Datei muss das folgende Format haben.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Der `Repositories` Schlüssel bezieht sich auf die Galerie, die aktiviert oder deaktiviert werden soll. Die Visual Studio-Galerie und die Beispielgalerie verwenden die folgenden Repository-GUIDs:

- Visual Studio Galerie : 0F45E408-7995-4375-9485-86B8DB553DC9

- Bilder Galerie : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Der `Disabled` Wert ist optional. Standardmäßig ist ein Katalog aktiviert.

  Der `Priority` Wert bestimmt die Reihenfolge, in der die Galerien im Dialogfeld **Optionen** aufgeführt sind. Visual Studio Gallery hat Priorität 10 und die Samples Gallery hat Priorität 20. Private Galerien beginnen bei Priorität 100. Wenn mehrere Galerien denselben Prioritätswert haben, wird die Reihenfolge, in `DisplayName` der sie angezeigt werden, durch die Werte ihrer lokalisierten Attribute bestimmt.

  Der `Protocol` Wert ist für Atom- oder SharePoint-basierte Galerien erforderlich.

  Entweder `DisplayName`muss `DisplayNameResourceID` entweder `DisplayNamePackageGuid`, oder beide und angegeben werden. Wenn alle angegeben sind, wird das `DisplayNameResourceID` und-Paar `DisplayNamePackageGuid` verwendet.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deaktivieren der Visual Studio-Galerie mithilfe einer .pkgdef-Datei
 Sie können einen Katalog in einer *.pkgdef-Datei* deaktivieren. Der folgende Eintrag deaktiviert die Visual Studio-Galerie:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Der folgende Eintrag deaktiviert den Beispielkatalog:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Weitere Informationen
- [Private Galerien](../extensibility/private-galleries.md)
