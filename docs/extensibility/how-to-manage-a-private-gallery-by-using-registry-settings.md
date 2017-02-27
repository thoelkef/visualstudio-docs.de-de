---
title: "Gewusst wie: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX-private Galerien verwalten"
  - "Verwalten von privaten Galerien VSIX"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Gewusst wie: Verwalten einer privaten Galerie mithilfe von Registrierungseinstellungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie ein Administrator oder Entwickler einer isolierte Shell\-Erweiterung sind, können Sie den Zugriff auf die Steuerelemente, Vorlagen und Tools in Visual Studio Gallery, die Samples Gallery oder private Galerien steuern. Damit einen Katalog verfügbar oder nicht verfügbar ist, erstellen Sie eine PKGDEF\-Datei, die die geänderte Registrierungsschlüssel und ihre Werte beschreibt.  
  
## Verwalten von privaten Galerien  
 Sie können eine PKGDEF\-Datei zum Steuern des Zugriffs auf die Galerien auf mehreren Computern erstellen. Diese Datei muss folgende Format haben.  
  
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
  
 Die `Repositories` Schlüssel verweist auf den Katalog aktiviert bzw. deaktiviert werden soll. Verwenden das folgende Repository GUIDs, der Visual Studio Gallery und die Samples Gallery:  
  
-   Visual Studio Gallery: 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   Samples Gallery: AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 Die `Disabled` Wert ist optional. Standardmäßig wird ein Katalog aktiviert.  
  
 Die `Priority` Wert bestimmt die Reihenfolge, in der die Kataloge im Dialogfeld "Optionen" aufgelistet sind. Visual Studio Gallery hat Priorität 10, und die Samples Gallery hat Priorität 20. Starten Sie private Kataloge Priorität 100. Wenn mehrere Kataloge denselben Prioritätswert aufweisen, wird die Reihenfolge der bestimmt, die Werte ihrer lokalisierten `DisplayName` Attribute.  
  
 Die `Protocol` für Atom\- oder SharePoint\-basierten Galerien ist erforderlich.  
  
 Entweder `DisplayName`, oder beide `DisplayNameResourceID` und `DisplayNamePackageGuid`, muss angegeben werden. Wenn all angegeben werden, und klicken Sie dann die `DisplayNameResourceID` und `DisplayNamePackageGuid` \-Paar wird verwendet.  
  
## Deaktivieren eine PKGDEF\-Datei mit Visual Studio Gallery  
 Sie können einen Katalog in eine PKGDEF\-Datei deaktivieren. Der folgende Eintrag wird der Visual Studio Gallery deaktiviert:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Der folgende Eintrag deaktiviert die Samples Gallery:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## Siehe auch  
 [Private Galerien](../extensibility/private-galleries.md)