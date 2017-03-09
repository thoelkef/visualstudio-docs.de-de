---
title: "Item cannot be added to the Toolbox. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_NOTSUPPORTEDDATA"
  - "vs.message.0x800A0065"
ms.assetid: 69fa5e73-bbc6-462c-95ca-bf2ee32d43ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Item cannot be added to the Toolbox.
Dieser Fehler tritt normalerweise auf, wenn Sie versuchen, ein Element hinzuzufügen, für das die Toolbox kein Verknüpfungssymbol anzeigen kann.  
  
 Die folgenden Elemente können in der Toolbox angezeigt werden:  
  
-   Auf dem lokalen Computer installierte Steuerelemente und .NET Framework\-Komponenten  
  
 **Hinweis** Bei Steuerelementen und Komponenten für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Web Forms muss die [AspNetHostingPermission.Level Property](https://msdn.microsoft.com/en-us/library/system.web.aspnethostingpermission.level.aspx)\-Eigenschaft "Unbegrenzt" festgelegt sein, damit sie in der Toolbox angezeigt werden.  
  
-   Ausgewählter Text, der aus einem Visual Studio\-Editor gezogen oder eingefügt wurde, z. B. Codeausschnitte.  
  
 Die folgenden Elemente können nicht in der Toolbox angezeigt werden:  
  
-   Excel\-Arbeitsmappendateien  
  
-   Auf freigegebenen Netzwerkservern installierte .NET Framework\-Assemblys  
  
    > [!NOTE]
    >  Eine über einen UNC\-Pfad hinzugefügte Assembly ist nicht voll vertrauenswürdig und verfügt daher nicht über die erforderlichen Berechtigungen, um in der Toolbox angezeigt zu werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der aktiven Toolbox\-Registerkarte im Dialogfeld **Toolbox anpassen** ein auf dem lokalen Computer installiertes Steuerelement bzw. eine Komponente hinzu.  
  
     \- oder \-  
  
2.  Ziehen Sie den markierten Text aus einem Visual Studio\-Editor in die Toolbox, oder fügen Sie ihn ein.  
  
## Siehe auch  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/de-de/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/de-de/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [Toolbox](../ide/reference/toolbox.md)