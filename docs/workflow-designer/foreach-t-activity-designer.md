---
title: "ForEach&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ForEach&lt;T&gt;-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.ForEach%601>\-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>\-Auflistung aus.  
  
## ForEach\-\<T\>\-Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>\-Aktivität.Der Standardwert lautet ForEach\<Int32\>.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden.Um die <xref:System.Activities.Statements.ForEach%601.Values%2A>\-Auflistung festzulegen, geben Sie im Feld **Werte** im **ForEach\<T\>**\-Aktivitätsdesigner oder im Eigenschaftenraster einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck ein.|  
|*TypeArgument*|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ForEach%601.Values%2A>\-Auflistung, der durch den generischen Parameter *T* angegeben wird.Standardmäßig ist *TypeArgument* auf **Int32** festgelegt.Sie ändern den Typ von *TypeArgument*, indem Sie im Kombinationsfeld des Eigenschaftenrasters einen anderen Wert auswählen.|  
  
 Standardmäßig hat der Schleifeniterator die Bezeichnung **item**.Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>\-Aktivitätsdesigner ändern.Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>\-Aktivität in Ausdrücken verwendet werden.  
  
## Siehe auch  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)