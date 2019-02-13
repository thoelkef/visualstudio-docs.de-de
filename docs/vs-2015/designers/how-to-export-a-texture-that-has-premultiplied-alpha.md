---
title: 'Vorgehensweise: Exportieren eine Textur, in der integrierte Alphakanäle verwendet | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7a06c1bfac60daabb9768b20b6047e99b3df3727
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757320"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Gewusst wie: Erstellen einer Textur, in der integrierte Alphakanäle verwendet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Pipeline für Bildinhalte können prämultiplizierte Alphatexturen aus einem Quellbild generiert werden. Diese können einfacher zu verwenden und robuster als Texturen ohne ein prämultipliziertes Alpha sein.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Konfigurieren des Quellbilds für die Verarbeitung mithilfe der Pipeline für Bildinhalte.  
  
-   Konfigurieren der Pipeline für Bildinhalte zum Generieren eines prämultiplizierten Alphas.  
  
## <a name="premultiplied-alpha"></a>Integrierte Alphakanäle  
 Prämultiplizierte Alphas bieten gegenüber konventionellen, nicht prämultiplizierten Alphas mehrere Vorteile, da sie die reale Interaktion des Lichts mit physischen Materialien besser darstellen, indem sie die Farbeinwirkung des Texels (der Farbe, die der Szene hinzugefügt wird) von seiner Durchsichtigkeit (die darunter liegende Farbe, die durchgelassen wird) trennen. Im Folgenden werden einige Vorteile von integrierten Alphakanälen beschrieben:  
  
-   Das Blending mit einem prämultiplizierten Alpha (Alphablending) ist ein assoziativer Vorgang. Das Blending mehrerer lichtdurchlässiger Texturen bringt unabhängig von der Reihenfolge, in der die Texturen gemischt werden, dasselbe Ergebnis.  
  
-   Wegen der assoziativen Art des Alphablendings, ist das Multi-Pass-Rendering von lichtdurchlässigen Objekten einfacher.  
  
-   Indem ein prämultipliziertes Alpha verwendet wird, können sowohl reines additives Blending (indem das Alpha auf null (0) festgelegt wird) und linear interpoliertes Blending gleichzeitig erreicht werden. In einem Partikelsystem kann ein additiv-gemischtes Feuerpartikel zu einem lichtdurchlässigen Rauchpartikel werden, das mithilfe von linearer Interpolation gemischt wird. Ohne prämultipliziertes Alpha müssten die Feuerpartikel separat aus den Rauchpartikeln gezogen und der Renderingzustand zwischen Aufrufen Auszugsaufrufen müsste geändert werden.  
  
-   In Texturen mit prämultipliziertem Alpha wird die Komprimierung in höherer Qualität durchgeführt als in Texturen ohne prämultipliziertes Alpha. Außerdem weisen sie keine entfärbten Ränder auf ("Halo-Effekt"), die beim Mischen von Texturen ohne prämultipliziertes Alpha auftreten können.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>So erstellen Sie eine Textur, in der integrierte Alphakanäle verwendet werden  
  
1. Beginnen Sie mit einer Standardtextur. Laden Sie eine vorhandene Datei, oder erstellen Sie eine, wie in [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben.  
  
2. Konfigurieren Sie die Texturdatei so, dass sie von der Pipeline für Bildinhalte verarbeitet wird. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die Texturdatei, und wählen Sie dann **Eigenschaften** aus. Legen Sie anschließend die Eigenschaft **Elementtyp** auf der Seite **Konfigurationseigenschaften**, **Allgemein** auf **Pipeline für Bildinhalte** fest. Stellen Sie sicher, dass die Eigenschaft **Inhalt** auf **JA** und die Option **Aus Build ausschließen** auf **NEIN** festgelegt ist. Wählen Sie dann die Schaltfläche **Übernehmen** aus. Die Eigenschaftenseite für die Konfiguration der **Pipeline für Bildinhalte** wird angezeigt.  
  
3. Konfigurieren Sie die Pipeline für Bildinhalte zum Generieren eines prämultiplizierten Alphas. Legen Sie die Eigenschaft **In prämultipliziertes Alphaformat konvertieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte** und **Allgemein** auf **Ja (/generatepremultipliedalpha)** fest.  
  
4. Klicken Sie auf die Schaltfläche **OK** .  
  
   Wenn Sie das Projekt erstellen, wird das Quellbild von der Pipeline für Bildinhalte vom Arbeitsformat in das angegebene Ausgabeformat konvertiert (Das schließt die Konvertierung des Bilds in ein prämultipliziertes Alphaformat ein). Das Ergebnis wird dann in das Ausgabeverzeichnis des Projekts kopiert.
