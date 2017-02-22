---
title: "Dialogfeld &#39;.NET-Typ suchen und ausw&#228;hlen&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "09/20/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeBrowser.UI"
  - "ActivityTypeResolver.UI"
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
caps.handback.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dialogfeld &#39;.NET-Typ suchen und ausw&#228;hlen&#39;
Wenn Sie im **Eigenschaftenfenster**, in Dialogfeldern oder Designern, z. B. dem Variablen\-Designer, in einer Listen mit Datentypen den Eintrag **Nach Typen suchen…** auswählen, wird das Dialogfeld **.NET\-Typ suchen und auswählen** angezeigt \(das auch kurz "Typbrowser" genannt wird\).In diesem Dialogfeld können Sie einen Typ aus der Strukturansicht der referenzierten Assemblys und Projekte auswählen.  
  
 Dieses Dialogfeld wird in einer Reihe von Benutzerszenarien wie dem Folgendem eingesetzt:  
  
-   Beim Festlegen des Typs einer Variable oder eines Arguments.  
  
-   Beim Auswählen eines Typs für eine generische Aktivität.  
  
-   Beim Hinzufügen einer catch\-Anweisung für die <xref:System.Activities.Statements.TryCatch>\-Aktivität.  
  
> [!NOTE]
>  Der Typbrowser kann verzweigte Visual Basic\-Arraytypen, aber keine mehrdimensionalen Arraytypen anzeigen.Ausführliche Informationen finden Sie unter [Verzweigte Arrays](http://go.microsoft.com/fwlink/?LinkId=195226) und [Mehrdimensionale Arrays](http://go.microsoft.com/fwlink/?LinkId=195227).  
  
## Auswählen eines Werts oder eines Verweistyps im Typbrowser  
  
#### So wählen Sie einen Wert\- oder Verweistyp im Typbrowser aus  
  
1.  Geben Sie im Feld **Typname** den Namen des Typs ein, den Sie verwenden möchten.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Sobald der Name des Typs, den Sie verwenden möchten, in der Struktur im Feld **Typname** angezeigt wird, doppelklicken Sie auf den Typ, um ihn auszuwählen.  
  
    -   Geben Sie genug Zeichen in das Feld **Typname** ein, um den Typ, den Sie verwenden möchten, eindeutig zu identifizieren, und drücken Sie dann die EINGABETASTE, um den Typ auszuwählen.  
  
#### So wählen Sie einen generischen Typ im Typbrowser aus  
  
1.  Geben Sie im Feld **Typname** den Namen des Typs ein, den Sie verwenden möchten.  
  
2.  Sobald der Name des Typs, den Sie verwenden möchten, in der Struktur im Feld **Typname** angezeigt wird, klicken Sie auf den Typ, um ihn auszuwählen und die betreffenden Dropdownfelder anzuzeigen.  
  
     Wählen Sie den Typ aus, den Sie verwenden möchten, um die Dropdownfelder zu schließen, und klicken Sie dann auf **OK**.  
  
## Typen, die im Typbrowser angezeigt werden  
 Welche Typen im Typbrowser angezeigt werden, hängt davon ab, wie der Typbrowser aufgerufen wurde.Wenn der Typbrowser von einem Workflowprojekt innerhalb von **vs2010** aus gestartet wurde, werden standardmäßig alle Typen der Assemblys und Projekte angezeigt, auf die dort verwiesen wird.Wenn der Typbrowser von außerhalb eines **vs2010**\-Projektsystems \(z. B. in einer neu gehosteten Workflowanwendung oder einer eigenständigen Workflowdatei\) gestartet wurde, dann werden standardmäßig die Typen von allen Assemblys angezeigt, die in die Anwendungsdomäne geladen wurden.  
  
 Die Typen im Typbrowser können von den Aktivitätsdesignerentwicklern gefiltert werden.Für jede gegebene Aktivität wird möglicherweise nur eine Teilmenge der Typen angezeigt.Zum Beispiel werden in der <xref:System.Activities.Statements.TryCatch>\-Aktivität nur die Typen, die von <xref:System.Exception> abgeleitet sind, im Typbrowser angezeigt.  
  
## Filter von Suchergebnissen im Typbrowser  
 Die Liste der Typen im Feld **Typname** wird kürzer, wie Sie mehr Zeichen eingeben, um eine Übereinstimmung zu finden.Nur Typen, deren vollqualifizierte Namen mit der eingegebenen Zeichenfolge beginnen, oder Typen, deren Kurzname mit der eingegebenen Zeichenfolge beginnen, erscheinen in der gefilterten Liste.  
  
 Beispiel:  
  
1.  Wenn Sie **Operation** eingeben, wird <xref:System.OperationCanceledException>, aber nicht <xref:System.InvalidOperationException> gefunden.Um <xref:System.InvalidOperationException> zu finden, geben Sie System.I oder Invalid ein.  
  
2.  Wenn Sie **Generic** eingeben, wird <xref:System.GenericUriParser>, aber nicht Typen im <xref:System.Collections.Generic>\-Namespace gefunden.Um nach Typen im <xref:System.Collections.Generic>\-Namespace zu suchen, geben Sie den vollqualifizierten Namen des Namespaces ein.  
  
## Auswählen eines Dienstvertrags mithilfe des Typbrowserdialogfelds  
 Beim Auswählen eines Dienstvertragstyps zeigt der Typbrowser nur Typen an, die über das <xref:System.ServiceModel.ServiceContractAttribute>\-Attribut verfügen.  
  
## Siehe auch  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)