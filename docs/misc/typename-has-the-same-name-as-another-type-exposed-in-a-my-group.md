---
title: "&quot;&lt;Typname&gt;&quot; hat den gleichen Namen, wie ein anderer in einer My-Gruppe verf&#252;gbar gemachter Typ. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Typname&gt;&quot; hat den gleichen Namen, wie ein anderer in einer My-Gruppe verf&#252;gbar gemachter Typ.
"\<Typname\>" hat den gleichen Namen, wie ein anderer in einer My\-Gruppe verfügbar gemachter Typ. Benennen Sie den Typ oder den einschließenden Namespace um.  
  
 Eine Klasse oder Struktur wird mit dem gleichen Namen wie eine Klasse oder Struktur in einem der `My`\-Objekte deklariert.  
  
 Ein Namenskonflikt  zwischen zwei Klassen, auf die über ein `My`\-Objekt \(z. B. `My.Forms`\) zugegriffen wird, konnte nicht vermieden werden.  
  
 Bei einem potenziellen Namenskonflikt zwischen Klassen in einem `My`\-Objekt ändert der Compiler den Eigenschaftennamen für den Typ von *Klassenname* zu *RootNamespace*\_*Namespace*\_*Klassenname*. Nehmen Sie z. B. zwei Formulare mit dem Namen `Form1`. Wenn sich eines dieser Formulare im Rootnamespace `WindowsApplication1` und im Namespace `Namespace1` befindet, würden Sie über `My.Forms.WindowsApplication1_Namespace1_Form1` auf das Formular zugreifen.  
  
 Dieser Fehler kann auftreten, wenn zwei Klassen den gleichen Namen haben, sich in geschachtelten Namespaces befinden und Namen mit Unterstrichen haben. Wenn der Compiler die neuen Eigenschaftennamen für die Klassen erstellt, gibt es  immer noch ein Namenskonflikt.  
  
 **Fehler\-ID:** BC36015  
  
### So beheben Sie diesen Fehler  
  
1.  Benennen Sie das neue Formular um.  
  
2.  Benennen Sie die Namespaces um.  
  
     Vermeiden Sie, einer Klasse oder Struktur den gleichen Namen zu geben, den eine vorhandene Klasse oder Struktur hat.  
  
## Siehe auch  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [NICHT IM BUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [My.Forms Object](/dotnet/visual-basic/language-reference/objects/my-forms-object)