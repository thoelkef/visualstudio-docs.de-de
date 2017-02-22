---
title: "Lokalisieren von VSIX-Paketen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lokalisieren von Paketen"
  - "Lokalisieren Sie die Erweiterung"
  - "Lokalisierte Bereitstellung"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Lokalisieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein VSIX\-Paket können lokalisiert werden, indem Sie eine Extension.vsixlangpack\-Datei für jede Zielsprache erstellen und die anschließende im richtigen Ordner. Wenn ein lokalisiertes Paket installiert ist, wird der lokalisierte Name der Erweiterung zusammen mit einer lokalisierten Beschreibung angezeigt. Wenn Sie angeben, eine lokalisierte Datei oder eine URL, die auf die lokalisierten Informationen verweist, werden sie ebenfalls angezeigt.  
  
 Wenn der Inhalt des VSIX\-Pakets ein VSPackage enthält, die fügt Menübefehlen oder eine andere Benutzeroberfläche finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren die neue UI\-Elemente.  
  
## Verzeichnisstruktur  
 Wenn ein Benutzer eine Erweiterung installiert **Erweiterungen und Updates** überprüft die oberste Ebene des VSIX\-Pakets für einen Ordner, deren Name das Visual Studio\-Gebietsschema des Zielcomputers übereinstimmt. Wenn **Erweiterungen und Updates** Auffinden eines .vsixlangpack\-Datei im Ordner, ersetzt er den lokalisierten Werte in der Datei für die entsprechenden Werte in die vsixmanifest\-Datei. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX\-Paket, das in Spanisch \(es\-ES\) und Französisch \(fr\-FR\) lokalisiert wird.  
  
 MyExtension.dll  
  
 "Extension.vsixmanifest"  
  
 \[Content\_Types\] .xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Die VSIX\-Unterstützung\-Projektvorlagen in den [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generieren Sie ein VSIX\-Manifest, und nennen Sie es "Source.Extension.vsixmanifest". Wenn Visual Studio das Projekt erstellt wurde, werden die Inhalte der Datei in "Extension.vsixmanifest" im VSIX\-Paket kopiert.  
  
## Die Extension.vsixlangpack\-Datei  
 Die Extension.vsixlangpack\-Datei der [Schema für VSIX\-Language Pack](../extensibility/vsx-language-pack-schema-reference.md). Dieses Schema ist ein [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) Root\-Element, und diese vier untergeordneten Elemente: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), und [Lizenz](../extensibility/license-element-vsix-language-pack-schema.md). Diese untergeordneten Elemente entsprechen den `Name`, `Description`, `MoreInfoURL`, und `License` untergeordnete Elemente von der `Identifier` \-Element der Datei "Extension.vsixmanifest".  
  
 Wenn Sie eine Vsixlangpack\-Datei erstellen, müssen Sie festlegen der `Include in Vsix` Eigenschaft `true`. Andernfalls wird die lokalisierter Installationstext ignoriert.  
  
#### Die Include in VSIX\-Eigenschaft festlegen  
  
1.  In **Projektmappen\-Explorer**, mit der rechten Maustaste auf die Extension.vsixlangpack\-Datei, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftenraster auf **Include in Vsix**, und legen Sie seinen Wert auf `true`.  
  
## Beispiel  
  
### Beschreibung  
 Das folgende Beispiel zeigt die relevanten Teile einer Datei "Extension.vsixmanifest" zusammen mit der entsprechenden Extension.vsixlangpack\-Datei für Spanisch. Die Werte des Language Packs ersetzen die Werte aus dem Manifest, wenn das Visual Studio\-Gebietsschema des Zielcomputers auf Spanisch festgelegt ist.  
  
### Code  
 \[Extension.vsixmanifest\]  
  
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
  
 \[Extension.vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## Siehe auch  
 [VSIX\-Sprachpaket\-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX\-Projektvorlage](../extensibility/vsix-project-template.md)