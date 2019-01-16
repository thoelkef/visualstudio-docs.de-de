---
title: Anzeigen von Arbeitsspeicher für Variablen im Debugger | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e56ad2c36e4b7a22cfb74e020c31e93f4846872
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837224"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Verwenden Sie das Fenster "Arbeitsspeicher" in Visual Studio-Debugger (C#, C++, Visual Basic F#)

Während des Debuggens die **Arbeitsspeicher** Fenster zeigt den Speicherplatz Ihrer app verwendet. 

Debuggerfenster wie **Watch**, **"Auto"**, **"lokal"**, und die **Schnellüberwachung** Dialogfeld wird angezeigt, Variablen, die auf bestimmten gespeichert werden die Speicherorte im Arbeitsspeicher. Die **Arbeitsspeicher** Fenster erfahren Sie, den gewonnenen Gesamteindruck berücksichtigen. Die Speicheransicht ist besonders angenehm beim Untersuchen von großer Datenmengen (Puffer oder umfangreiche Zeichenfolgen, z. B.), die nicht auch in den anderen Fenstern angezeigt werden. 

Die **Arbeitsspeicher** Fenster nicht auf die Anzeige von Daten beschränkt ist. Alles, was in den Speicherplatz, einschließlich Daten, Code und zufällig verteilte Objekte in nicht zugewiesenem Arbeitsspeicher angezeigt.  

Die **Arbeitsspeicher** Fenster nicht für Skriptsprachen oder SQL-debugging verfügbar ist. Diesen Sprachen erkannt nicht das Konzept des Arbeitsspeichers.  
  
## <a name="open-a-memory-window"></a>Öffnen Sie ein Fenster "Arbeitsspeicher"  
  
Anderen Debuggerfenster wie die **Arbeitsspeicher** Windows nur während einer Debugsitzung zur Verfügung stehen. 

>[!IMPORTANT]
>So aktivieren Sie die **Arbeitsspeicher** Windows **Debuggen auf Adressebene aktivieren** muss ausgewählt werden **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen** > **allgemeine**. 

**So öffnen Sie ein Arbeitsspeicherfenster**
  
1. Stellen Sie sicher, dass **Debuggen auf Adressebene aktivieren** ausgewählt ist **Tools** > **Optionen** (oder **Debuggen**  >  **Optionen**) > **Debuggen** > **allgemeine**. 
   
1. Debuggen starten, indem Sie den grünen Pfeil auswählen drücken **F5**, oder wählen Sie **Debuggen** > **Debuggen starten**.  
   
2. Klicken Sie unter **Debuggen** > **Windows** > **Arbeitsspeicher**Option **Arbeitsspeicher 1**, **Arbeitsspeicher 2**, **Arbeitsspeicher 3**, oder **Arbeitsspeicher 4**. (Einige Editionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bieten nur eine **Arbeitsspeicher** Fenster.)  

## <a name="move-around-in-the-memory-window"></a>Navigieren Sie in das Fenster "Arbeitsspeicher"  

Der Adressraum eines Computers ist groß und leicht verloren gehen können Ihre aktuelle Position einen Bildlauf der **Arbeitsspeicher** Fenster. 

Höhere Speicheradressen werden unten im Fenster angezeigt. Um eine höhere Adresse anzuzeigen, scrollen Sie nach unten. Um eine niedrigere Adresse anzuzeigen, scrollen Sie nach oben.  

Wechseln Sie sofort zu einer bestimmten Adresse in der **Arbeitsspeicher** Fenster mithilfe von Drag & Drop oder durch Eingabe der Adresse in der **Adresse** Feld. Die **Adresse** Feld akzeptiert, alphanumerische Adressen und -Ausdrücke, wie z. B. Adressen ausgewertet `e.User.NonroamableId`. 

Erzwingen Sie sofortige erneute Auswertung eines Ausdrucks in der **Adresse** Feld, wählen Sie den gerundet Pfeil **automatisch neu auswerten** Symbol. 

In der Standardeinstellung die **Arbeitsspeicher** Fenster behandelt **Adresse** Ausdrücke als live-Ausdrücke, erneut ausgewertet, wenn die app ausgeführt wird. Live-Ausdrücke hilfreich, z. B., den Arbeitsspeicher anzuzeigen, der durch eine Zeigervariable berührt wird.  

**Ziehen und ablegen, um an einem Speicherort zu verschieben:**  
   
1. Wählen Sie in einem Debuggerfenster eine Speicheradresse oder eine Zeigervariable, die eine Speicheradresse enthält.  
   
2. Drag & drop die Adresse oder den Zeiger in den **Arbeitsspeicher** Fenster. Diese Adresse wird dann der **Adresse** Feld, und die **Arbeitsspeicher** Fenster angepasst wird, um die Adresse der oben angezeigt. 
  
**Um an einem Speicherort zu verschieben, indem Sie sie in das Adressfeld eingeben:**
  
- Geben oder fügen Sie die Adresse oder den Ausdruck in der **Adresse** Feld, und drücken Sie **EINGABETASTE**, oder wählen sie in der Dropdownliste in der **Adresse** Feld. Die **Arbeitsspeicher** Fenster angepasst wird, um die Adresse der oben angezeigt.
  
## <a name="customize-the-memory-window"></a>Passen Sie das Fenster "Arbeitsspeicher" 

In der Standardeinstellung Speicherinhalt angezeigt als 1-Byte-Ganzzahlen im Hexadezimalformat angegeben werden, und die Fensterbreite bestimmt die Anzahl der Spalten angezeigt. Die Art und Weise der Anzeige des Speicherinhalts im Fenster **Arbeitsspeicher** kann angepasst werden.  
  
**So ändern Sie das Format des Speicherinhalts:**  
  
-  Mit der rechten Maustaste den **Arbeitsspeicher** Fenster, und wählen Sie die Formate, die Sie möchten, aus dem Kontextmenü.  
  
**So ändern Sie die Anzahl der Spalten im Fenster „Arbeitsspeicher“:**
  
- Wählen Sie den Dropdownpfeil neben der **Spalten** ein, und wählen Sie die Anzahl der Spalten, um anzuzeigen, oder wählen Sie **automatisch** für automatische Anpassung basierend auf Fensterbreite.  
  
Wenn Sie nicht, dass der Inhalt des möchten der **Arbeitsspeicher** Fenster ändern, wie Ihre app ausgeführt wird, können Sie die live-ausdrucksauswertung deaktivieren. 

**So schalten Sie die Liveauswertung um:**  
  
- Mit der rechten Maustaste den **Arbeitsspeicher** , und wählen **automatisch neu auswerten** im Kontextmenü. 

  >[!NOTE]
  >Live-Ausdruck ist eine Umschaltoption Auswertung und ist standardmäßig so auswählen **automatisch neu auswerten** ausgeschaltet. Auswählen von **automatisch neu auswerten** wird er erneut wieder eingeschaltet. 
  
Die Symbolleiste am oberen Rand des Fensters **Arbeitsspeicher** kann angezeigt oder ausgeblendet werden. Sie müssen nicht den Zugriff auf die **Adresse** Feld oder eine andere Tools, wenn die Symbolleiste ausgeblendet ist.  
  
**Um die Anzeige der Symbolleiste zu wechseln:**  
  
- Mit der rechten Maustaste den **Arbeitsspeicher** , und wählen **Symbolleiste anzeigen** im Kontextmenü. Je nach ihrem vorherigen Zustand wird die Symbolleiste ein- bzw. ausgeblendet.  
  
## <a name="follow-a-pointer-through-memory"></a>Führen Sie einen Zeiger im Arbeitsspeicher  

In systemeigenen Code-apps können Sie als live-Ausdrücke Registernamen. Zur Verfolgung des Stapels können Sie z. B. den Stapelzeiger verwenden.  
  
**So verfolgen Sie einen Zeiger im Arbeitsspeicher:**
  
1. In der **Arbeitsspeicher** Fenster **Adresse** Geben Sie einen Zeigerausdruck, der im aktuellen Bereich ist. Je nach verwendeter Sprache müssen Sie u. U. den entsprechenden Verweis aufheben.  
  
2. Drücken Sie die **EINGABETASTE**.  
   
   Verwendung einem Debugbefehl wie z. B. **Schritt**, die Speicheradresse angezeigt, der **Adresse** Feld- und am oberen Rand der **Arbeitsspeicher** Fenster wird automatisch als der Zeiger ändert ändert.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)