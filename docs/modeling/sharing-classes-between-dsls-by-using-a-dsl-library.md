---
title: "Gemeinsame Nutzung von Klassen durch DSLs &#252;ber eine DSL-Bibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# Gemeinsame Nutzung von Klassen durch DSLs &#252;ber eine DSL-Bibliothek
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualisierung und Modellieren SDK können Sie eine unvollständige DSL\-Definition erstellen, die Sie in ein anderes DSL importieren können.  Auf diese Weise können Sie allgemeine Teile des Faktors ähnliche Modelle.  
  
## Erstellen und Verwenden DSL\-Bibliotheken  
  
#### So erstellen Sie eine DSL\-Bibliothek  
  
1.  Erstellen Sie ein neues DSL\-Projekt, und wählen Sie die Vorlage DSL\-Bibliotheks Office\-Lösungen fehl.  
  
     Ein einzelnes DSL\-Projekt wird mit einem leeren Modell erstellt.  
  
2.  Sie können Klassen von Domänen, Beziehungen usw. Forms hinzufügen.  
  
     Die Elemente in der Bibliothek müssen eine einzelne Mithilfe von eingebetteten Struktur nicht besteht.  
  
     Um eine Beziehung zu definieren, das Importer verwenden können, erstellen Sie zwei Domänen und Klassen erstellen Sie die Beziehung zwischen ihnen.  
  
     Erwägen Sie, **Vererbungsmodifizierer** der Domänen zu Klassen `Abstract`festzulegen.  
  
3.  Sie können Elemente, die Sie in DSL\-Explorer definieren, wie Verbindungs\-Generatoren hinzufügen.  
  
4.  Sie können Anpassungen, die zusätzlichen Code erfordern das Validierungseinschränkungen hinzufügen.  
  
5.  Klicken Sie auf **Alle Vorlagen transformieren**.  
  
6.  Erstellen Sie das Projekt.  
  
7.  Wenn Sie das DSL verteilen, damit andere Personen verwenden, müssen Sie die kompilierte Assembly \(DLL\) und die Datei `DslDefinition.dsl`bereitstellen.  Sie können die kompilierte Assembly in einem Ordner unter `Dsl\bin\*`suchen  
  
#### So erstellen Sie eine DSL\-Bibliothek importieren  
  
1.  In einer anderen DSL\-Definition in **DSL\-Explorer**, klicken Sie mit der rechten Maustaste auf die Stammklasse des DSL, und klicken Sie dann auf **Neuen DslLibrary\-Import hinzufügen**.  
  
2.  Legen Sie im Eigenschaftenfenster **Dateipfad** der Bibliothek fest.  Sie können entweder einen absoluten oder relativen Pfad verwenden.  
  
     Die importierte Bibliothek wird in DSL\-Explorer, im schreibgeschützten Modus.  
  
3.  Sie können die importierten Klasse als Basisklasse verwenden.  Erstellen Sie eine Domänenklasse im importierten DSL aus, und legen Sie im Eigenschaftenfenster **Basisklasse** zu einer importierten Klasse.  
  
4.  Klicken Sie auf Alle Vorlagen transformieren.  
  
5.  Fügen Sie dem DSL\-Projekt einen Verweis auf die Assembly hinzu \(DLL\) DSL\-Bibliotheks die durch das Projekt erstellt wurde.  
  
6.  Erstellen Sie die Projektmappe.  
  
 Eine DSL\-Bibliothek kann andere Bibliotheken importieren.  Wenn Sie eine Bibliothek importieren, werden seine Importe als auch automatisch in DSL\-Explorer.  
  
## Siehe auch  
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)