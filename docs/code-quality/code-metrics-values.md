---
title: "Codemetrikwerte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codemetrik"
  - "Codeanalyse"
  - "Messen der Codequalität"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
caps.handback.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Codemetrikwerte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten.  Die Codemetrikergebnisse vermitteln Entwicklern ein Verständnis dafür, welche Typen und\/oder Methoden überarbeitet oder gründlicher getestet werden sollten.  Entwicklerteams können potenzielle Risiken erkennen, den aktuellen Zustand eines Projekts feststellen und den Fortschritt bei der Softwareentwicklung verfolgen.  
  
## Softwaremaßstäben  
 Die folgende Liste enthält die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] berechneten Codemetrikergebnisse:  
  
-   **Wartbarkeitsindex** – Berechnet einen relativen Indexwert zwischen 0 und 100, der angibt, wie einfach der Code zu verwalten ist.  Ein hoher Wert steht für bessere Verwaltbarkeit.  Mit farbcodierten Bewertungen können problematische Stellen im Code schnell ermittelt werden.  Eine grüne Bewertung liegt zwischen 20 und 100 und gibt an, dass der Code über ein gute Wartbarkeit verfügt.  Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code über eine mäßige Wartbarkeit verfügt.  Eine rote Bewertung liegt zwischen 0 und 9 und gibt eine niedrige Wartbarkeit an.  
  
-   **Zyklomatische Komplexität** – Misst die strukturelle Komplexität des Codes.  Sie wird durch Berechnung der Anzahl unterschiedlicher Codepfade im Programmfluss erstellt.  Für ein Programm mit komplexer Ablaufsteuerung sind mehr Komponententests erforderlich, wenn eine gute Codeabdeckung erzielt werden soll, zudem verschlechtert sich die Verwaltbarkeit.  
  
    > [!NOTE]
    >  In einigen Fällen unterscheidet sich die Berechnung der zyklomatischen Komplexität einer Methode in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] von der Berechnung in früheren Versionen.  Weitere Informationen finden Sie unter [Problembehandlung für Codemetrikfehler](../code-quality/troubleshooting-code-metrics-issues.md) im Abschnitt "Änderungen in den Visual Studio 2010\-Berechnungen für die Codekomplexität".  
  
-   **Vererbungstiefe** – Gibt die Anzahl der Klassendefinitionen an, die sich bis zum Stamm der Klassenhierarchie erstrecken.  Je tiefer die Hierarchie, umso schwieriger ist u. U. zu erkennen, wo bestimmte Methoden und Felder definiert oder\/und neu definiert werden.  
  
-   **Klassenkopplung** – Misst die Kopplung an eindeutige Klassen durch Parameter, lokale Variablen, Rückgabetypen, Methodenaufrufe, generische oder Vorlageninstanziierungen, Basisklassen, Schnittstellenimplementierungen, für externe Typen definierte Felder sowie Attributdekorationen.  Gute Softwareentwürfe zeichnen sich durch Typen und Methoden mit hoher Kohäsion und loser Kopplung aus.  Eine enge Kopplung deutet auf einen Entwurf hin, der aufgrund zahlreicher gegenseitiger Abhängigkeiten zwischen anderen Typen nur schwer wiederzuverwenden und zu verwalten ist.  
  
-   **Codezeilen** – Gibt die ungefähre Anzahl von Zeilen im Code an.  Da die Anzahl auf dem IL\-Code basiert, entspricht der Wert nicht der exakten Anzahl von Zeilen in der Quellcodedatei.  Ein sehr hoher Wert kann darauf hinweisen, dass ein Typ oder eine Methode zu viele Aufgaben ausführt und aufgeteilt werden sollte.  Er könnte auch darauf hindeuten, dass der Typ oder die Methode schwierig zu verwalten ist.  
  
## Anonyme Methoden  
 Eine *anonyme Methode* ist einfach eine Methode ohne Namen.  Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben.  Metrikergebnisse für eine anonyme Methode, die in einem Member deklariert ist, z. B. als Methode oder Accessor, sind mit dem Member verknüpft, der die Methode deklariert.  Mit dem Member, der die Methode aufruft, sind sie nicht verknüpft.  
  
 Weitere Informationen dazu, wie anonyme Methoden in der Codemetrik behandelt werden, finden Sie unter [Anonyme Methoden und Codeanalyse](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## Generierter Code  
 Einige Softwaretools und \-compiler generieren Code, der einem Projekt hinzugefügt wird und für den Projektentwickler entweder nicht sichtbar ist oder von ihm nicht geändert werden sollte.  In den meisten Fällen wird generierter Code bei der Berechnung der Metrikwerte von der Codemetrik ignoriert.  Auf diese Weise spiegeln die Metrikwerte nur den Code wider, der vom Entwickler eingesehen und geändert werden kann.  
  
 Für Windows Forms generierter Code wird nicht ignoriert, da dieser Code vom Entwickler angezeigt und geändert werden kann.  
  
## Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)