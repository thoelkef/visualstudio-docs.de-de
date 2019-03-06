---
title: Anpassen von Beschriftungen für datengebundene Steuerelemente
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1745aef29da9fc8efd49789f0112c903128f6f74
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323699"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio

Beim Ziehen von Elementen aus der [Fenster "Datenquellen"](add-new-data-sources.md#data-sources-window) auf einen Designer, der eine besondere Überlegungen kommt ins Spiel: die Spaltennamen in den sind neu formatiert, in eine lesbarere Zeichenfolge, wenn zwei oder mehr Wörter gefunden werden verkettet.

::: moniker range="vs-2017"

Sie können anpassen, dass die Möglichkeit, in dem diese Bezeichnungen, durch Festlegen erstellt werden, der **SmartCaptionExpression**, **SmartCaptionReplacement**, und **SmartCaptionSuffix** Werte im die **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designer** Registrierungsschlüssel.

::: moniker-end

::: moniker range=">=vs-2019"

Sie können anpassen, dass die Möglichkeit, in dem diese Bezeichnungen, durch Festlegen erstellt werden, der **SmartCaptionExpression**, **SmartCaptionReplacement**, und **SmartCaptionSuffix** Werte im die **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designer** Registrierungsschlüssel.

::: moniker-end

> [!NOTE]
> Dieser Registrierungsschlüssel ist nicht vorhanden, bis Sie ihn erstellen.

Smart-captioning wird gesteuert, mit dem regulären Ausdruck eingegeben haben, in den Wert des der **SmartCaptionExpression** Wert. Hinzufügen der **Datendesigner** Registrierungsschlüssel überschreibt die standardmäßige regulären Ausdruck, der Beschriftungstitel gesteuert. Weitere Informationen zu regulären Ausdrücken finden Sie unter [mithilfe von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Die folgende Tabelle beschreibt die Registrierungswerte, die die Beschriftung Bezeichnungen zu steuern.

|Registrierungselement|Beschreibung|
|-------------------|-----------------|
|**SmartCaptionExpression**|Der reguläre Ausdruck, die, den Sie verwenden, um Ihre Muster übereinstimmen.|
|**SmartCaptionReplacement**|Das Format, das Gruppen angezeigt werden die **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Eine optionale Zeichenfolge zum Anfügen an das Ende der Beschriftung.|

In der folgende Tabelle sind die internen Standardeinstellungen für diese Registrierungswerte aufgeführt.

|Registrierungselement|Standardwert|Erklärung|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Entspricht einem Kleinbuchstaben Zeichen gefolgt von einem Großbuchstaben oder ein Unterstrich.|
|**SmartCaptionReplacement**|**$1 $2**|Die **$1** stellt alle Zeichen in der ersten Klammern für den Ausdruck übereinstimmen und die **$2** stellt alle Zeichen in der zweiten Klammer übereinstimmt. Der Austausch ist die erste Übereinstimmung, ein Leerzeichen und die zweite Übereinstimmung.|
|**SmartCaptionSuffix**|**:**|Stellt ein Zeichen, die an die zurückgegebene Zeichenfolge angefügt. Wenn die Beschriftung wird z. B. `Company Name`, erleichtert das Suffix `Company Name:`|

> [!CAUTION]
> Seien Sie vorsichtig, wenn alles in den Registrierungs-Editor ausführen. Sichern Sie die Registrierung vor der Bearbeitung. Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können zu schwerwiegende Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Microsoft garantiert nicht, dass Probleme, die Sie auslösen, indem Sie eine nicht ordnungsgemäße Verwendung des Registrierungs-Editors behoben werden können. Verwenden Sie den Registrierungs-Editor auf eigene Gefahr.
>
> Informationen zum Sichern, bearbeiten und Wiederherstellen der Registrierungs finden Sie unter [Windows-Registrierungsinformationen für fortgeschrittene Benutzer](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Ändern des Verhaltens der intelligenten Untertitel im Datenquellen-Fenster

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.

2. Typ `regedit` in die **ausführen** (Dialogfeld), und klicken Sie auf **OK**.

3. Erweitern Sie die **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**Knoten.

::: moniker range="vs-2017"

4. Mit der rechten Maustaste die **15.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Mit der rechten Maustaste die **16.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

::: moniker-end

5. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie drei neue Zeichenfolgenwerte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Mit der rechten Maustaste die **SmartCaptionExpression** Wert ein, und wählen Sie **ändern**.

7. Geben Sie den regulären Ausdruck sollen die **Datenquellen** Fenster verwenden.

8. Mit der rechten Maustaste die **SmartCaptionReplacement** Wert ein, und wählen Sie **ändern**.

9. Geben Sie die Ersetzung formatierte Zeichenfolge die Möglichkeit, die den regulären Ausdruck übereinstimmenden Muster angezeigt werden soll.

10. Mit der rechten Maustaste die **SmartCaptionSuffix** Wert ein, und wählen Sie **ändern**.

11. Geben Sie alle Zeichen, die am Ende der Beschriftung angezeigt werden sollen.

    Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** , die Beschriftungstitel werden erstellt unter Verwendung der neuen Registrierungswerte bereitgestellt.

## <a name="turn-off-the-smart-captioning-feature"></a>Deaktivieren Sie die intelligenten Untertitel-Funktion

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.

2. Typ `regedit` in die **ausführen** (Dialogfeld), und klicken Sie auf **OK**.

3. Erweitern Sie die **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**Knoten.

::: moniker range="vs-2017"

4. Mit der rechten Maustaste die **15.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Mit der rechten Maustaste die **16.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.

::: moniker-end

5. Mit der rechten Maustaste die **Datendesigner** Knoten, und erstellen Sie drei neue Zeichenfolgenwerte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Mit der rechten Maustaste die **SmartCaptionExpression** Element aus, und wählen Sie **ändern**.

7. Geben Sie `(.*)` für den Wert. Dadurch wird die gesamte Zeichenfolge übereinstimmen.

8. Mit der rechten Maustaste die **SmartCaptionReplacement** Element aus, und wählen Sie **ändern**.

9. Geben Sie `$1` für den Wert. Dies ersetzt die Zeichenfolge, mit der übereinstimmende Wert, der die gesamte Zeichenfolge ist, sodass es unverändert bleiben.

    Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** Fenster werden die Beschriftungstitel mit unveränderter Beschriftung erstellt.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)