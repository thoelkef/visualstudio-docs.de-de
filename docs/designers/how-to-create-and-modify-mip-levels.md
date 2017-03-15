---
title: "Gewusst wie: Erstellen und &#196;ndern von MIP-Ebenen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Erstellen und &#196;ndern von MIP-Ebenen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument veranschaulicht, wie Sie die **Bildbearbeitung** verwenden, um *MIP\-Ebenen* für die Detailebene Texturraum zu generieren und zu ändern.  
  
## Generieren von MIP\-Ebenen  
 *Mipmapping* ist eine Technik, die verwendet wird, um Renderingvorgänge zu beschleunigen und Aliasingartefakte auf strukturierten Objekten zu reduzieren, indem mehrere Kopien einer Textur in unterschiedlichen Größen vorberechnet und gespeichert werden.  Jede als MIP\-Ebene bezeichnete Kopie hat die halbe Breite und halbe Höhe der vorherigen Kopie.  Wenn eine Textur auf der Oberfläche eines Objekts gerendert wird, wird die MIP\-Ebene, die am ehesten dem Bildraumbereich der strukturierten Oberfläche entspricht, automatisch ausgewählt.  Das bedeutet, dass die Grafikhardware übergroße Texturen nicht filtern muss, um für eine konsistente visuelle Qualität zu sorgen.  Die Arbeitsspeicherkosten zum Speichern der MIP\-Ebenen sind zwar ca. 33 Prozent höher als für die Originaltextur allein, die Leistungssteigerung und die bessere Bildqualität rechtfertigen diese Kosten jedoch.  
  
#### So generieren Sie MIP\-Ebenen  
  
1.  Beginnen Sie mit einer einfachen Textur, wie unter [Gewusst wie: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben.  Um bestmögliche Ergebnisse zu erzielen, geben Sie eine Textur an, deren Breite und Höhe der Potenz 2 entsprechen, z. B. 256, 512, 1024 usw.  
  
2.  Generieren Sie die MIP\-Ebenen.  Wählen Sie auf der Symbolleiste **Bildbearbeitungsmodus** die Option **Erweitert**, **Tools**, **MIPS generieren** aus.  
  
     Beachten Sie, dass die Schaltflächen **Zur nächsten MIP\-Ebene wechseln** und **Zur vorherigen MIP\-Ebene wechseln** jetzt auf der Symbolleiste **Bildbearbeitungsmodus** angezeigt werden.  Wenn das Fenster **Eigenschaften** angezeigt wird, beachten Sie auch, dass die schreibgeschützten Eigenschaften **Mip\-Ebene** und **Anzahl der Mip\-Ebenen** nun in den Bildeigenschaften angezeigt werden.  
  
## Ändern von MIP\-Ebenen  
 Um Spezialeffekte zu erzielen oder die Bildqualität auf bestimmten Detailebenen zu erhöhen, können Sie jede MIP\-Ebene einzeln ändern.  Beispielsweise können Sie einem strukturierten Objekt ein anderes Erscheinungsbild in einem bestimmten Abstand geben \(größerer Abstand entspricht kleineren MIP\-Ebenen\). Oder Sie können sicherstellen, dass Texturen, die Text oder Symbole enthalten, sogar auf kleineren MIP\-Ebenen lesbar bleiben.  
  
#### So ändern Sie eine einzelne MIP\-Ebene  
  
1.  Wählen Sie die MIP\-Ebene aus, die Sie ändern möchten.  Klicken Sie auf der Symbolleiste **Bildbearbeitungsmodus** auf die Schaltflächen **Zur nächsten MIP\-Ebene wechseln** und **Zur vorherigen MIP\-Ebene wechseln**, um zwischen den MIP\-Ebenen zu navigieren.  
  
2.  Nachdem Sie die MIP\-Ebene ausgewählt haben, die Sie ändern möchten, können Sie die Zeichenwerkzeuge verwenden, um sie zu ändern, ohne den Inhalt anderer MIP\-Ebenen zu ändern.  Die Zeichenwerkzeuge sind auf der Symbolleiste **Bildbearbeitung** verfügbar.  Nachdem Sie ein Tool ausgewählt haben, können Sie seine Eigenschaften im Fenster **Eigenschaften** ändern.  Informationen zu den Zeichentools und ihren Eigenschaften finden Sie unter [Grafik\-Editor](../designers/image-editor.md).  
  
> [!NOTE]
>  Wenn eine Änderung der Inhalte der einzelnen MIP\-Ebenen \(wie zum Erreichen bestimmter Effekte\) nicht erforderlich ist, wird empfohlen, Mipmaps zur Buildzeit aus der Quelltextur zu generieren.  Dies hilft, sicherzustellen, dass MIP\-Ebenen synchron mit der Quelltextur bleiben, da Änderungen an einer MIP\-Ebene nicht automatisch an andere Ebenen weitergegeben werden.  Weitere Informationen zur Generierung von Mipmaps zur Buildzeit finden Sie unter [Gewusst wie: Erstellen einer Textur, die Mipmaps enthält](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md)