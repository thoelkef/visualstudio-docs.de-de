---
title: Element "extern" | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d4559aa03af16faf955594c3850281e6cf7b4903
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="extern-element"></a>Extern-Element
Das Element "extern" verweist auf externe Headerdateien (. h), um zum Zeitpunkt der Kompilierung mit der VSCT-Datei zusammengeführt. Die Dateien, die zusammengeführt werden muss auf dem Include-Pfad angegeben, dem VSCT-Compiler oder mithilfe einer [Include-Element](../extensibility/include-element.md). Die Dateien möglicherweise andere VSCT-Dateien oder C++-Headerdateien.  
  
 Definitionen in Headerdateien muss im Format "#define [Symbol] [Value]" der Wert kann ein anderes Symbol sein, wenn es zuvor definiert wurde. Definitionen können in bedingten Anweisungen Befehl Elemente verwendet werden. Jedes Symbol nicht verwendet werden, werden verworfen.  
  
 CommandTable-Element  
Extern-Element  
  
## <a name="syntax"></a>Syntax  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|href|Erforderlich. Der Pfad der Headerdatei:<br /><br /> href="stdidcmd.h"|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Dies ist optional. Die Standardsprache für alle [ \<Zeichenfolgen >](../extensibility/strings-element.md) Elemente in der Befehlstabelle:<br /><br /> Language = "En-us"|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine|Keine|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen – d. h. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern –, die eine VSPackage für die IDE bereitstellt.|  
  
## <a name="example"></a>Beispiel  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
