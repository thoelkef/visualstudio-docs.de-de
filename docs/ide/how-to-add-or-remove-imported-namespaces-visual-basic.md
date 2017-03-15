---
title: "Gewusst wie: Hinzuf&#252;gen oder Entfernen von importierten Namespaces (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Hinzufügen importierter Namespaces"
  - "Importierte Namespaces [Visual Studio]"
  - "Namespaces [Visual Studio], Importiert"
  - "Verweise [Visual Studio], Importierte Namespaces"
  - "Entfernen importierter Namespaces"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Gewusst wie: Hinzuf&#252;gen oder Entfernen von importierten Namespaces (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch das Importieren eines Namespaces können Sie Elemente aus diesem Namespace im Code verwenden, ohne das Element vollständig zu kennzeichnen.  Wenn Sie z. B. auf die `Create`\-Methode in der `System.Messaging.MessageQueue`\-Klasse zugreifen möchten, können Sie den `System.Messaging`\-Namespace importieren und auf das im Code benötigte Element einfach als `MessageQueue.Create` verweisen.  
  
 Importierte Namespaces werden auf der Seite **Verweise** des **Projekt\-Designers** verwaltet.  Die in diesem Dialogfeld angegebenen Importe werden direkt an den Compiler \(`/imports`\) übergeben und betreffen alle Dateien im Projekt.  Verwenden Sie die `Imports`\-Anweisung, um einen Namespace in einer einzigen Quellcodedatei zu verwenden.  
  
### So fügen Sie einen importierten Namespace hinzu  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf den Knoten **Mein Projekt** für das Projekt.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Verweise**.  
  
3.  Aktivieren Sie in der Liste **Importierte Namespaces** das Kontrollkästchen für den Namespace, den Sie hinzufügen möchten.  
  
    > [!NOTE]
    >  Damit er importiert werden kann, muss sich der Namespace in einer Komponente befinden, auf die verwiesen wird.  Falls der Namespace nicht in der Liste aufgeführt ist, müssen Sie einen Verweis auf die Komponente hinzufügen, in der er enthalten ist.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### So entfernen Sie einen importierten Namespace  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf den Knoten **Mein Projekt** für das Projekt.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Verweise**.  
  
3.  Deaktivieren Sie in der Liste **Importierte Namespaces** das Kontrollkästchen für den Namespace, den Sie entfernen möchten.  
  
## Benutzerimporte  
 Mithilfe von Benutzerimporten können Sie anstelle des gesamten Namespaces eine bestimmte Klasse innerhalb eines Namespaces importieren.  Möglicherweise verfügt eine Anwendung über einen Import für den `Systems.Diagnostics`\-Namespace, aber die einzige Klasse in diesem Namespace, die für Sie von Interesse ist, ist die `Debug`\-Klasse.  Sie können `System.Diagnostics.Debug` als Benutzerimport definieren und dann den Import für `System.Diagnostics` entfernen.  
  
 Falls Sie Ihre Meinung später ändern und entscheiden, dass Sie eher die `EventLog`\-Klasse benötigt hätten, könnten Sie `System.Diagnostics.EventLog` als Benutzerimport eingeben und `System.Diagnostics.Debug` mithilfe der Aktualisierungsfunktion überschreiben.  
  
#### So fügen Sie einen Benutzerimport hinzu  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf den Knoten **Mein Projekt** für das Projekt.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Verweise**.  
  
3.  Geben Sie im Textfeld unterhalb der Liste **Importierte Namespaces** den vollständigen Namen des zu importierenden Namespaces einschließlich des Stammnamespaces ein.  
  
4.  Klicken Sie auf die Schaltfläche **Benutzerimport hinzufügen**, um den Namespace der Liste **Importierte Namespaces** hinzuzufügen.  
  
    > [!NOTE]
    >  Wenn der Namespace mit einem bereits in der Liste enthaltenen Namespace übereinstimmt, ist die Schaltfläche **Benutzerimport hinzufügen** deaktiviert, da ein Import nicht zweimal hinzugefügt werden kann.  
  
#### So aktualisieren Sie einen Benutzerimport  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf den Knoten **Mein Projekt** für das Projekt.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Verweise**.  
  
3.  Wählen Sie aus der Liste **Importierte Namespaces** den Namespace aus, den Sie ändern möchten.  
  
4.  Geben Sie im Textfeld unterhalb der Liste **Importierte Namespaces** den Namen für den neuen Namespace ein.  
  
5.  Klicken Sie auf die Schaltfläche **Benutzerimport aktualisieren**, um den Namespace in der Liste **Importierte Namespaces** zu aktualisieren.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)