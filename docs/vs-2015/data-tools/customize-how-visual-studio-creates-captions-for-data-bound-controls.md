---
title: Anpassen, wie Visual Studio 2015 Beschriftungen für datengebundene Steuerelemente erstellt | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 549fa4842a4e57043ddac90683d05383b7c3d44d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693926"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Ziehen von Elementen aus der [Fensters "Datenquellen"](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf den Windows Forms-Designer, der eine besondere Überlegungen kommt ins Spiel: die Spaltennamen in den sind neu formatiert, in eine lesbarere Zeichenfolge, wenn zwei oder mehr Wörter sind miteinander verkettete gefunden Sie werden. Sie können anpassen, dass die Möglichkeit, die in der diese Bezeichnungen, durch Festlegen erstellt werden der **SmartCaptionExpression**, **SmartCaptionReplacement**, und **SmartCaptionSuffix** Werte im die **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data Designer** Registrierungsschlüssel.

> [!NOTE]
> Dieser Registrierungsschlüssel ist nicht vorhanden, bis Sie ihn erstellen.

 Smart-captioning wird gesteuert, mit dem regulären Ausdruck eingegeben haben, in den Wert des der **SmartCaptionExpression** Wert. Hinzufügen der **Datendesigner** Registrierungsschlüssel überschreibt die standardmäßige regulären Ausdruck, der Beschriftungstitel gesteuert. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Die folgende Tabelle beschreibt die Registrierungswerte, die die Beschriftung Bezeichnungen zu steuern.

|Registrierungselement|Beschreibung|
|-------------------|-----------------|
|**SmartCaptionExpression**|Der reguläre Ausdruck verwendet, um Ihre Muster übereinstimmen.|
|**SmartCaptionReplacement**|Das Format, das Gruppen angezeigt werden die **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Eine optionale Zeichenfolge zum Anfügen an das Ende der Beschriftung.|

 In der folgende Tabelle sind die internen Standardeinstellungen für diese Registrierungswerte aufgeführt.

|Registrierungselement|Standardwert|Erklärung|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll})(\\\p{Lu})&#124;_+|Entspricht einem Kleinbuchstaben Zeichen gefolgt von einem Großbuchstaben oder ein Unterstrich.|
|**SmartCaptionReplacement**|$1 $2|Die $1 stellt alle Zeichen in der ersten Klammern des Ausdrucks übereinstimmen und $2 stellt alle Zeichen in der zweiten Klammer übereinstimmt. Der Austausch ist die erste Übereinstimmung, ein Leerzeichen und die zweite Übereinstimmung.|
|**SmartCaptionSuffix**|:|Stellt ein Zeichen, die an die zurückgegebene Zeichenfolge angefügt. Wenn die Beschriftung wird z. B. `Company Name`, erleichtert das Suffix `Company Name:`|

> [!CAUTION]
> Sie sollten sehr vorsichtig, wenn alles in den Registrierungs-Editor ausführen können. Sichern Sie die Registrierung vor der Bearbeitung. Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können zu schwerwiegende Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Microsoft garantiert nicht, dass Probleme, die Sie auslösen, indem Sie eine nicht ordnungsgemäße Verwendung des Registrierungs-Editors behoben werden können. Verwenden Sie den Registrierungs-Editor auf eigene Gefahr.
>
> Im folgenden Knowledge Base-Artikel enthält Anweisungen zum Sichern, bearbeiten und Wiederherstellen der Registrierung: [Beschreibung der Microsoft Windows-Registrierung](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; En-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>So ändern Sie das intelligente Untertitel Verhalten des Fensters Datenquellen

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.

2. Typ `regedit` in die **ausführen** (Dialogfeld), und klicken Sie auf **OK**.

3. Erweitern Sie die **HKEY_CURRENT_USER** Knoten.

4. Erweitern Sie die **Software** Knoten.

5. Erweitern Sie die **Microsoft** Knoten.

6. Erweitern Sie die **VisualStudio** Knoten.

7. Mit der rechten Maustaste die **10.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

8. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionExpression`.

9. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionReplacement`.

10. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionSuffix`.

11. Mit der rechten Maustaste die **SmartCaptionExpression** Element aus, und wählen Sie **ändern**.

12. Geben Sie den regulären Ausdruck sollen die **Datenquellen** Fenster verwenden.

13. Mit der rechten Maustaste die **SmartCaptionReplacement** Element aus, und wählen Sie **ändern**.

14. Geben Sie die Ersetzung formatierte Zeichenfolge die Möglichkeit, die den regulären Ausdruck übereinstimmenden Muster angezeigt werden soll.

15. Mit der rechten Maustaste die **SmartCaptionSuffix** Element aus, und wählen Sie **ändern**.

16. Geben Sie alle Zeichen, die am Ende der Beschriftung angezeigt werden sollen.

     Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** , die Beschriftungstitel werden erstellt unter Verwendung der neuen Registrierungswerte bereitgestellt.

### <a name="to-turn-off-the-smart-captioning-feature"></a>So deaktivieren Sie die intelligenten Untertitel-Funktion

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.

2. Typ `regedit` in die **ausführen** (Dialogfeld), und klicken Sie auf **OK**.

3. Erweitern Sie die **HKEY_CURRENT_USER** Knoten.

4. Erweitern Sie die **Software** Knoten.

5. Erweitern Sie die **Microsoft** Knoten.

6. Erweitern Sie die **VisualStudio** Knoten.

7. Mit der rechten Maustaste die **10.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

8. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionExpression`.

9. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionReplacement`.

10. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie ein neues **Zeichenfolgenwert** mit dem Namen `SmartCaptionSuffix`.

11. Mit der rechten Maustaste die **SmartCaptionExpression** Element aus, und wählen Sie **ändern**.

12. Geben Sie `(.*)` für den Wert. Dadurch wird die gesamte Zeichenfolge übereinstimmen.

13. Mit der rechten Maustaste die **SmartCaptionReplacement** Element aus, und wählen Sie **ändern**.

14. Geben Sie `$1` für den Wert. Dies ersetzt die Zeichenfolge, mit der übereinstimmende Wert, der die gesamte Zeichenfolge ist, sodass es unverändert bleiben.

     Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** Fenster werden die Beschriftungstitel mit unveränderter Beschriftung erstellt.

## <a name="see-also"></a>Siehe auch
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
