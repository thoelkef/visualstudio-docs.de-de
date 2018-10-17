---
title: Bitmap-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfade1c45e7299450a47c290d3746e4e36817319
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231518"
---
# <a name="bitmap-element"></a>Bitmap-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert eine Bitmap. Die Bitmap wird von einer Ressource oder aus einer Datei geladen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID der Befehls-ID der GUID-ID.<br /><br /> Das Guid-Attribut für eine Bitmap ist nicht in jedem VSPackage oder andere Befehlsgruppe zugeordnet.  Es sollte für die bitmapdefinition eindeutig sein und sollte nicht für andere Zwecke verwendet werden.|  
|"RESID"|ID des Befehls-ID der GUID-ID. Entweder der "RESID" oder das Href-Attribut ist erforderlich.<br /><br /> Das ResID-Attribut ist ein Integer-Ressourcen-ID, die den bitmapstrip bestimmt, der während der Zusammenführung Befehlstabelle geladen werden soll.  Beim Laden der Befehlstabelle ist, wird die Bitmaps angegeben werden, indem Sie die Ressourcen-ID aus der Ressource des gleichen Moduls geladen werden.|  
|"usedlist"|Erforderlich, wenn das ResID-Attribut vorhanden ist. Wählt die verfügbaren Images im bitmapstrip.|  
|href|Der Pfad für die Bitmap. Entweder der "RESID" oder das Href-Attribut ist erforderlich.<br /><br /> Für die angegebene Abbilddatei, die in die resultierende Binärdatei eingebettet ist, wird dem Includepfad durchsucht.  Beim Befehl Tabelle Zusammenführen wird das Bild kopiert, und ist keine zusätzliche Ressourcensuche oder Laden erforderlich.  Wenn das Attribut "usedlist" nicht vorhanden ist, stehen alle Bilder auf den Streifen. **Hinweis:** Images können in verschiedenen Formaten, die BMP-, GIF- und PNG enthalten bereitgestellt werden.  Frühere Versionen des Compilers wurde Bitmap mit 32-Bit-Images, die alpha-Information für die partielle Transparenz, nicht unterstützt. Die problemumgehung für diese Versionen ist das PNG-Format verwendet.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Elemente der Bitmap.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

