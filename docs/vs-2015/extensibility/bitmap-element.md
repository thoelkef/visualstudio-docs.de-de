---
title: Bitmap-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184749"
---
# <a name="bitmap-element"></a>Bitmap-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert eine Bitmap. Die Bitmap wird entweder aus einer Ressource oder aus einer Datei geladen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID des GUID-/ID-befehlsbezeichners.<br /><br /> Das GUID-Attribut für eine Bitmap ist keinem VSPackage oder einer anderen Befehlsgruppe zugeordnet.  Er sollte für die Bitmapdefinition eindeutig sein und sollte nicht für andere Zwecke verwendet werden.|  
|resID|ID des GUID-/ID-befehlsbezeichners. Entweder die Resid oder das href-Attribut ist erforderlich.<br /><br /> Das Attribut Resid ist eine ganzzahlige Ressourcen-ID, die den bitmapstrip bestimmt, der während der Zusammenführung der Befehls Tabelle geladen werden soll.  Beim Laden der Befehls Tabelle werden die durch die Ressourcen-ID angegebenen Bitmaps aus der Ressource des gleichen Moduls geladen.|  
|usedlist|Erforderlich, wenn das Resid-Attribut vorhanden ist. Wählt die verfügbaren Bilder in der bitmapleiste aus.|  
|href|Der Pfad zur Bitmap. Entweder die Resid oder das href-Attribut ist erforderlich.<br /><br /> Der Include-Pfad wird nach der angezeigten Bilddatei durchsucht, die in die resultierende Binärdatei eingebettet ist.  Während der Zusammenführung der Befehls Tabelle wird das Image kopiert, und es ist keine zusätzliche Ressourcen Suche oder-Auslastung erforderlich.  Wenn das usedlist-Attribut nicht vorhanden ist, sind alle Images im Strip verfügbar. **Hinweis:**  Bilder können in einem von mehreren Formaten angegeben werden, die BMP, PNG und GIF enthalten.  Frühere Versionen des Compilers unterstützten keine 32-Bit-Bitmapbilder, die Alpha Informationen für partielle Transparenz enthielten. Die Problem Umgehung für diese Versionen besteht darin, das PNG-Format zu verwenden.|  
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
