---
title: Microsoft Language Interface Packs (LIPs) und Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: f72b67216ef0403af2e1f97208a7e33daa09b9b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179282"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Microsoft Language Interface Packs (LIPs) und Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Windows Multilingual User Interface Packs (LIP) können Sie eine Sprachversion von Windows und anschließend verschiedene Sprachpakete für die Benutzeroberfläche installieren. Sprachpakete für die Benutzeroberfläche stellen eine lokalisierte Benutzeroberfläche für das Betriebssystem bereit. Beispielsweise können Sie ein japanisches Sprachpaket für die Benutzeroberfläche über einer englischsprachigen Windows-Version installieren und dann zwischen den Windows-Benutzeroberflächensprachen Japanisch und Englisch umschalten. Mit LIP können Sie mehrere Sprachversionen von Windows auf einem Computer installieren.  
  
 Auf Computern mit installierten LIPs und mehreren Sprachversionen von Visual Studio werden durch Änderungen der Einstellungen für die Windows-Anzeigesprache sowohl Windows- als auch Visual Studio-Einstellungen festgelegt, wenn entsprechende Sprachpakete installiert sind.  
  
## <a name="limitations-of-multi-language-installations"></a>Einschränkungen von mehrsprachigen Installationen  
 Wenn Sie verschiedene Sprachversionen von Visual Studio auf demselben Computer installieren, können Sie nur zwischen Sprachen entsprechender Editionen umschalten. Wenn beispielsweise eine englische Express Edition, eine deutsche Express Edition und eine Professional Edition installiert sind, können Sie nur zwischen den Sprachen der Express Editions, nicht aber die der Professional Edition umschalten.  
  
 Visual Studio verwendet ein einheitliches Sprachpaket. Um mehr als eine Sprachversion dieser Produkte zu installieren, müssen Sie das vollständige Sprachenprodukt zuerst installieren und dann ein oder mehrere Sprachpakete einrichten.  
  
> [!NOTE]
>  Visual Studio unterstützt nicht die Installation mehrerer Sprachversionen des vollständigen Sprachenprodukts auf demselben Computer. Wenn Sie ein vollständiges Sprachenprodukt installiert haben, müssen Sie die Sprachversionen mithilfe von Sprachpaketen hinzufügen. Sie können immer noch mehrere vollständige Sprachenprodukte der Express-Editionen auf demselben Computer installieren.  
  
### <a name="support-for-code-pages"></a>Unterstützung für Codepages  
 In einigen Visual Studio-Tools wird Text nicht korrekt angezeigt, wenn er Zeichen enthält, die nicht in der aktuellen Codepage verfügbar sind. Stattdessen werden Fragezeichen oder fehlerhafter Text angezeigt. Die folgenden Tools oder Bereiche sind betroffen:  
  
-   Über FTP bereitgestellte Websites  
  
-   Computernamen mit Nicht-ASCII-Zeichen in einigen Steuerelementen.  
  
-   Außerhalb von Visual Studio ausgeführte Befehlszeilentools  
  
-   Visual Basic-Assistent für die Migration  
  
-   Testcontainer für ActiveX-Steuerelemente  
  
-   OLE/COM-Objektkatalog  
  
-   ISAPI-Webdebugtool  
  
-   MFC-Anwendungsprojekte mit HTML-Hilfeinhalt  
  
-   Die Visual SourceSafe/SCCI-Benutzeroberfläche schaltet bei einer nicht kompatiblen Codepage automatisch auf Englisch zurück.  
  
-   Visual SourceSafe unterstützt keine Unicode-Dateinamen.  
  
-   Vom Endbenutzer definierte Zeichen (private gebrauchte Zone) können nicht als Token/Bezeichner verwendet werden.  
  
-   Erweiterte Lateinisch-B-Zeichen können in einigen Visual Studio-Toolfenstern nicht angezeigt werden, wenn die Windows-Codepage auf eine ostasiatische Sprache festgelegt ist.  
  
-   Bei Lauftexten, die aus Zeichen von mehreren Sprachskripts bestehen, wird möglicherweise das standardmäßige Symbol für einige Zeichen angezeigt.  
  
-   Das Kopieren und Einfügen von komplexen Skriptzeichenfolgen in allgemeine Steuerelemente bewirkt möglicherweise, dass die Zeichenstrukturierung verloren geht. Geben Sie Text stattdessen über die entsprechende Sprachtastatur ein.  
  
##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>So zeigen Sie nicht in der aktuellen Codepage enthaltene Zeichen ordnungsgemäß an  
  
1.  Klicken Sie auf **starten**, klicken Sie auf **Systemsteuerung**, und öffnen Sie dann **Regions- und Sprachoptionen** (oder **Region** in [!INCLUDE[win8](../includes/win8-md.md)]).  
  
    > [!NOTE]
    >  Sie müssen auf dem Computer als Administrator angemeldet sein, um die folgenden Schritte auszuführen.  
  
2.  Klicken Sie auf die Registerkarte **Erweitert**.  
  
3.  In der **wählen Sie die Sprachversion der Programme ohne Unicodeunterstützung überein, Sie verwenden möchten** wählen die Sprache, die Sie derzeit verwenden.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Ändern der in Visual Studio für den Benutzeroberflächen-Text verwendeten Sprache  
 Bei der Installation mehrerer Sprachversionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf demselben Computer ausführen, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Benutzeroberfläche standardmäßig auf **wie Microsoft Windows**. Diese Einstellung gibt an, dass [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird der Text der Benutzeroberfläche angezeigt, in der Sprache, die der Anzeigesprache des Betriebssystems angegeben wird.  
  
> [!NOTE]
>  Wenn Visual Studio festgelegt ist, verwenden **wie Microsoft Windows**, und das entsprechende Sprachpaket für Visual Studio nicht installiert ist, verwendet Visual Studio die Sprache des ersten Visual Studio-Installation.  
  
#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>So legen Sie die in Visual Studio für den Benutzeroberflächentext verwendete Sprache fest  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie **Umgebung** , und klicken Sie dann auf **internationale Einstellungen**.  
  
3.  In der **Sprache** Sprache auswählen, die in der der Text der Benutzeroberfläche angezeigt werden sollte in der Entwicklungsumgebung.  
  
     Um Text für die Benutzeroberfläche in der IDE-Übereinstimmung der Betriebssystem-Anzeigesprache festgelegt haben, wählen Sie **wie Microsoft Windows**.  
  
 Sie können auch den devenv-Befehl verwenden, um die Sprache festzulegen, die für Benutzeroberfläche verwendet wird. Weitere Informationen finden Sie unter [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Internationale Einstellungen, Umgebung, Dialogfeld „Optionen“](../ide/reference/international-settings-environment-options-dialog-box.md)