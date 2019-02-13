---
title: 'Vorgehensweise: Exportieren einer Textur für die Verwendung mit Direct2D- oder JavaScript-Apps | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d5858df00057298f961189173a3943f3e23d2b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781479"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Gewusst wie: Exportieren einer Textur für die Verwendung mit Direct2D- oder Javascript-Apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Pipeline für Bildinhalte können Texturen generiert werden, die mit den internen Renderingkonventionen von Direct2D kompatibel sind. Texturen dieser Art sind für die Verwendung bei Apps, die Direct2D nutzen und in Windows Store-Apps, die mithilfe von JavaScript erstellt werden, geeignet.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Konfigurieren des Quellbilds für die Verarbeitung mithilfe der Pipeline für Bildinhalte.  
  
-   Konfigurieren der Pipeline für Bildinhalte zur Generierung einer Textur, die in einer Direct2D- oder JavaScript-App verwenden werden kann.  
  
    -   Generieren einer blockkomprimierten DDS-Datei.  
  
    -   Generieren eines prämultiplizierten Alphas.  
  
    -   Generieren von Mipmaps deaktivieren.  
  
## <a name="rendering-conventions-in-direct2d"></a>Renderingkonventionen in Direct2D  
 Texturen, die im Direct2D-Kontext verwendet werden, müssen diesen internen Direct2D-Renderingkonventionen entsprechen:  
  
-   Direct2D implementiert Transparenz und Durchsichtigkeit, indem ein prämultipliziertes Alpha verwendet wird. Die mit Direct2D verwendeten Texturen müssen ein multipliziertes Alpha enthalten, selbst wenn für die Textur weder Transparenz noch Durchsichtigkeit verwendet wird. Weitere Informationen zu integrierten Alphakanälen finden Sie unter [Vorgehensweise: Erstellen einer Textur, in der integrierte Alphakanäle verwendet werden](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   Die Textur muss in DDS-Format angegeben werden, indem eines dieser Blockkomprimierungsformate verwendet wird:  
  
    -   BC1_UNORM-Komprimierung  
  
    -   BC2_UNORM-Komprimierung  
  
    -   BC3_UNORM-Komprimierung  
  
-   Mipmaps werden nicht unterstützt.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>So erstellen Sie eine Textur, die mit den Renderingkonventionen von Direct2D kompatibel ist  
  
1. Beginnen Sie mit einer Standardtextur. Laden Sie ein vorhandenes Bild, oder erstellen Sie ein neues, wie in [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben. Um die Blockkomprimierung im DDS-Format zu unterstützen, geben Sie eine Textur an, deren Breite und Höhe ein Vielfaches von vier ist, beispielsweise 100 x 100, 128 x 128 oder 256 x 192. Da Mipmapping nicht unterstützt wird, muss die Textur nicht quadratisch und keine Potenz von zwei sein.  
  
2. Konfigurieren Sie die Texturdatei so, dass sie durch die Pipeline für Bildinhalte verarbeitet wird. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die soeben erstellte Texturdatei, und wählen Sie dann **Eigenschaften** aus. Legen Sie anschließend die Eigenschaft **Elementtyp** auf der Seite **Konfigurationseigenschaften**, **Allgemein** auf **Pipeline für Bildinhalte** fest. Stellen Sie sicher, dass die Eigenschaft **Inhalt** auf **JA** und die Option **Aus Build ausschließen** auf **NEIN** festgelegt ist. Wählen Sie dann die Schaltfläche **Übernehmen** aus. Die Eigenschaftenseite für die Konfiguration der **Pipeline für Bildinhalte** wird angezeigt.  
  
3. Legen Sie das Ausgabeformat auf eines der blockkomprimierten Formate fest. Legen Sie die Eigenschaft **Komprimieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte**, **Allgemein** auf **BC3_UNORM-Komprimierung (/compress:BC3_UNORM)** fest. Sie können abhängig von Ihren Anforderungen eines der anderen BC1-, BC2- oder BC3-Formate auswählen. Von Direct2D werden aktuell die Texturen "BC4", "BC5", "BC6" bzw. "BC7" nicht unterstützt. Weitere Informationen zu den verschiedenen BC-Formate finden Sie unter [Blockkomprimierung (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
   > [!NOTE]
   >  Das Format der Datei, die von der Pipeline für Bildinhalte erzeugt wird, legt das angegebene Komprimierungsformat fest. Dieses unterscheidet sich von der Eigenschaft **Format** des Quellbilds in der Bildbearbeitung, mit dem das Format der auf dem Datenträger gespeicherten Quellbilddatei festgelegt wird – und zwar als *Arbeitsformat*. Normalerweise möchten Sie nicht, dass ein Arbeitsformat komprimiert wird.  
  
4. Konfigurieren Sie die Pipeline für Bildinhalte so, dass sie eine Ausgabe mit integrierten Alphakanälen erzeugt. Legen Sie die Eigenschaft **In prämultipliziertes Alphaformat konvertieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte** und **Allgemein** auf **Ja (/generatepremultipliedalpha)** fest.  
  
5. Konfigurieren Sie die Pipeline für Bildinhalte so, dass sie keine Mipmaps generiert. Legen Sie die Eigenschaft **MIPS generieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte**, **Allgemein** auf **Nein** fest.  
  
6. Klicken Sie auf die Schaltfläche **OK** .  
  
   Wenn Sie das Projekt erstellen, wird das Quellbild von der Pipeline für Bildinhalte vom Arbeitsformat in das angegebene Ausgabeformat konvertiert (Die Konvertierung schließt die Generierung prämultiplizierter Alphas ein). Das Ergebnis wird dann in das Ausgabeverzeichnis des Projekts kopiert.
