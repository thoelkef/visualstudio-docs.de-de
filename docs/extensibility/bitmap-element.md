---
title: Bitmap-Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb265aabdb4feda05512e036cda19abc574e2fd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-element"></a>Bitmapelement
Definiert eine Bitmap an. Die Bitmap wird aus einer Ressource oder aus einer Datei geladen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID des Bezeichners GUID-ID-Befehl.<br /><br /> Das Guid-Attribut für eine Bitmap ist nicht verknüpft mit jeder VSPackage oder andere Befehlsgruppe.  Es sollte eindeutig sein, um die bitmapdefinition und sollte nicht für andere Zwecke verwendet werden.|  
|resID|ID des Bezeichners GUID-ID-Befehl. Die ResID oder Href-Attribut ist erforderlich.<br /><br /> Das ResID-Attribut ist ein Integer-Ressourcen-ID, die die Bitmap-Menüleiste bestimmt, die beim Zusammenführen von Befehlstabelle geladen werden soll.  Wenn die Befehlstabelle geladen wird, wird die Bitmaps, angegeben durch die Ressourcen-ID aus der Ressource des gleichen Moduls geladen werden.|  
|usedList|Erforderlich, wenn das Attribut ResID vorhanden ist. Wählt verfügbaren Images auf den Bitmap-Streifen.|  
|href|Der Pfad für die Bitmap. Die ResID oder Href-Attribut ist erforderlich.<br /><br /> Die Include-Pfad wird für die angegebene Abbilddatei durchsucht, die in die resultierende Binärdatei eingebettet ist.  Während der Befehl Tabelle Zusammenführen wird das Bild kopiert, und zusätzliche Ressourcensuche oder Load sind nicht erforderlich.  Wenn das UsedList-Attribut nicht vorhanden ist, stehen alle Bilder auf den Streifen. **Hinweis:** Bilder können in einem von mehreren Formaten, die z. bmp, PNG und GIF b. bereitgestellt werden.  Frühere Versionen des Compilers hat keine 32-Bit-Bitmapbilder unterstützt, die für die partielle Transparenz Alphainformationen hatte. Die problemumgehung für diese Versionen ist das PNG-Format verwendet.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert die Elemente mithilfe einer Bitmap.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)