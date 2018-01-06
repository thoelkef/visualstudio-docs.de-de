---
title: "Anpassen, wie Visual Studio Beschriftungen für datengebundene Steuerelemente erstellt | Microsoft Docs"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 60d98d6b8cefc2f7fb7829d841001f92bd9063de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Passen Sie an, wie Visual Studio Beschriftungen für datengebundene Steuerelemente erstellt
Beim Ziehen von Elementen aus der [Datenquellenfenster](add-new-data-sources.md) in einem Designer muss eine besondere kommt es zu einem: die Spaltennamen in der Beschriftung Bezeichnungen werden neu formatiert, in eine lesbarere Zeichenfolge, wenn zwei oder mehr Wörter gefunden werden verkettet. Sie können ändern, wie in der folgenden Bezeichnungen, durch Festlegen erstellt werden der **SmartCaptionExpression**, **SmartCaptionReplacement**, und **SmartCaptionSuffix** Werte die **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designer** Registrierungsschlüssel.  
  
> [!NOTE]
> Dieser Registrierungsschlüssel ist nicht vorhanden, bis Sie ihn erstellen.  
  
Smart-captioning wird gesteuert, mit dem regulären Ausdruck, der den Wert des eingegebenen der **SmartCaptionExpression** Wert. Hinzufügen der **Daten-Designer** Registrierungsschlüssel überschreibt standardmäßig regulären Ausdruck, der Beschriftungstitel gesteuert. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
Die folgende Tabelle beschreibt die Registrierungswerte, die Beschriftung Bezeichnungen zu steuern.  
  
|Registrierungselement|Beschreibung|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|Der reguläre Ausdruck verwendet, um Ihre Muster übereinstimmen.|  
|**SmartCaptionReplacement**|Das Format zum Anzeigen von Gruppen der **SmartCaptionExpression**.|  
|**SmartCaptionSuffix**|Eine optionale Zeichenfolge, an das Ende der Beschriftung angefügt werden soll.|  
  
In der folgenden Tabelle sind die internen Standardeinstellungen für diese Registrierungswerte aufgeführt.  
  
|Registrierungselement|Standardwert|Erklärung|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124; _ +|Entspricht einem Kleinbuchstaben Zeichen, gefolgt von einem Großbuchstaben oder ein Unterstrich.|  
|**SmartCaptionReplacement**|$1 $2|$1 stellt keine Zeichen in der ersten Klammer des Ausdrucks übereinstimmen, und $2 stellt keine Zeichen in der zweiten Klammern abgeglichen. Der Ersatz erfolgt die erste Übereinstimmung, ein Leerzeichen und dann die zweite Übereinstimmung.|  
|**SmartCaptionSuffix**|:|Stellt ein Zeichen, die an die zurückgegebene Zeichenfolge angefügt. Angenommen, die Beschriftung wird `Company Name`, erleichtert das Suffix`Company Name:`|  
  
> [!CAUTION]
> Sie sollten sich genau überlegen, wenn nichts im Registrierungs-Editor ausführen können. Sichern Sie die Registrierung vor der Bearbeitung. Wenn Sie den Registrierungs-Editor falsch verwenden, können zu schwerwiegende Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich sind. Microsoft garantiert nicht, dass Probleme, die mithilfe des Registrierungs-Editors nicht ordnungsgemäß aufgelöst werden können. Verwenden Sie den Registrierungs-Editor auf eigene Gefahr.  
>   
>  Im folgende Knowledge Base-Artikel enthält Anweisungen zum Bearbeiten, Sichern und Wiederherstellen der Registrierung: [Beschreibung der Microsoft Windows-Registrierung](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (Http://support.microsoft.com/default.aspx?scid=kb;en-us; 256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>So ändern Sie das intelligente Untertiteln Verhalten der im Fenster "Datenquellen"  
  
1.  Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.  
  
2.  Typ `regedit` in der **ausführen** (Dialogfeld), und klicken Sie auf **OK**.  
  
3.  Erweitern Sie die **HKEY_CURRENT_USER**, **Software*, **Microsoft**, **VisualStudio** Knoten.  
  
7.  Mit der rechten Maustaste die **15.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.  
  
8.  Mit der rechten Maustaste die **Daten-Designer** Knoten, und erstellen Sie drei neue Zeichenfolgenwerte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. Mit der rechten Maustaste die **SmartCaptionExpression** Wert ein, und wählen Sie **ändern**.  
  
12. Geben Sie den regulären Ausdruck sollen die **Datenquellen** Fenster verwenden.  
  
13. Mit der rechten Maustaste die **SmartCaptionReplacement** Wert ein, und wählen Sie **ändern**.  
  
14. Geben Sie die Ersetzung Zeichenfolge formatiert die Methode, die den regulären Ausdruck übereinstimmenden Muster angezeigt werden soll.  
  
15. Mit der rechten Maustaste die **SmartCaptionSuffix** Wert ein, und wählen Sie **ändern**.  
  
16. Geben Sie alle Zeichen, die am Ende der Beschriftung angezeigt werden sollen.  
  
    Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** Fenster die Beschriftungstitel sind erstellt mithilfe der neuen Registrierungswerte bereitgestellt.  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>So deaktivieren Sie die smart Untertiteln-Funktion  
  
1.  Öffnen Sie ein Befehlsfenster, indem Sie auf **starten** und dann **ausführen**.  
  
2.  Typ `regedit` in der **ausführen** (Dialogfeld), und klicken Sie auf **OK**.  
  
3.  Erweitern Sie die **HKEY_CURRENT_USER**, **Software**, **Microsoft**, **VisualStudio** Knoten.  
  
7.  Mit der rechten Maustaste die **15.0** Knoten, und erstellen Sie ein neues **Schlüssel** mit dem Namen `Data Designers`.  
  
8.  Mit der rechten Maustaste die **Daten-Designer** Knoten, und erstellen Sie drei neue Zeichenfolgenwerte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. Mit der rechten Maustaste die **SmartCaptionExpression** -Element aus, und wählen Sie **ändern**.  
  
12. Geben Sie `(.*)` für den Wert. Dadurch wird die gesamte Zeichenfolge übereinstimmen.  
  
13. Mit der rechten Maustaste die **SmartCaptionReplacement** -Element aus, und wählen Sie **ändern**.  
  
14. Geben Sie `$1` für den Wert. Dies ersetzt die Zeichenfolge mit den übereinstimmenden Wert, der die gesamte Zeichenfolge so, dass unverändert bleiben.  
  
    Das nächste Mal ziehen Sie Elemente aus der **Datenquellen** Fenster werden die Beschriftungstitel mit unveränderter Beschriftung erstellt.  
  
## <a name="see-also"></a>Siehe auch  
[Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)