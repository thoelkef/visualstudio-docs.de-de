---
title: Lokalisieren von VSIX-Paketen | Microsoft-Dokumentation
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
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bad0b3307e4b0e5358bd04d4990d0012685300d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523465"
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Lokalisieren von VSIX-Paketen](https://docs.microsoft.com/visualstudio/extensibility/localizing-vsix-packages).  
  
Sie können ein VSIX-Paket lokalisieren, indem eine Extension.vsixlangpack-Datei für jede Sprache Ziel erstellen und die anschließende im richtigen Ordner. Wenn ein lokalisiertes Paket installiert ist, wird der lokalisierte Name der Erweiterung zusammen mit einer lokalisierten Beschreibung angezeigt. Wenn Sie angeben, eine lokalisierte Lizenzdatei oder eine URL, die auf lokalisierte Informationen verweist, werden sie ebenfalls angezeigt.  
  
 Wenn der Inhalt des VSIX-Pakets eine VSPackage enthält, die fügt Menübefehle oder eine andere Benutzeroberfläche, finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren die neue UI-Elemente.  
  
## <a name="directory-structure"></a>Verzeichnisstruktur  
 Wenn ein Benutzer eine Erweiterung installiert **Erweiterungen und Updates** überprüft die oberste Ebene der VSIX-Paket für einen Ordner, deren Name mit der Visual Studio-Gebietsschema des Zielcomputers übereinstimmt. Wenn **Erweiterungen und Updates** eine .vsixlangpack findet Datei im Ordner "", die lokalisierte Werte in dieser Datei für die entsprechenden Werte in die vsixmanifest-Datei ersetzt. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-ES) und Französisch (fr-FR) lokalisiert ist.  
  
 MyExtension.dll  
  
 "Extension.vsixmanifest"  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Die VSIX-unterstützt-Projektvorlagen in der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generieren Sie ein VSIX-Manifest, und nennen Sie sie "Source.Extension.vsixmanifest". Wenn Visual Studio das Projekt erstellt wurde, kopiert er den Inhalt der Datei in "Extension.vsixmanifest" im VSIX-Paket.  
  
## <a name="the-extensionvsixlangpack-file"></a>Die Extension.vsixlangpack-Datei  
 Die Extension.vsixlangpack-Datei der [Schema für das VSIX-Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md). Dieses Schema verfügt über eine [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) Root-Element, und diese vier untergeordneten Elemente: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), und [Lizenz](../extensibility/license-element-vsix-language-pack-schema.md). Diese untergeordneten Elemente entsprechen den `Name`, `Description`, `MoreInfoURL`, und `License` untergeordnete Elemente des der `Identifier` -Element der Datei "Extension.vsixmanifest".  
  
 Wenn Sie eine Vsixlangpack-Datei erstellen, müssen Sie festlegen der `Include in Vsix` Eigenschaft `true`. Andernfalls wird der Text für die lokalisierte Installations-ignoriert.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Die Include in VSIX-Eigenschaft festlegen  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Extension.vsixlangpack-Datei, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftenraster auf **Include in VSIX-Datei**, und legen Sie dessen Wert auf `true`.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt die relevanten Teile einer Datei "Extension.vsixmanifest", zusammen mit der entsprechenden Extension.vsixlangpack-Datei für Spanisch. Die Werte aus dem Sprachpaket ersetzen die Werte aus dem Manifest auf, wenn das Visual Studio-Gebietsschema des Zielcomputers auf Spanisch festgelegt ist.  
  
### <a name="code"></a>Code  
 ["Extension.vsixmanifest"]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSIX-LanguagePack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Projektvorlage](../extensibility/vsix-project-template.md)

