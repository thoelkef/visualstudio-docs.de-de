---
title: Gliedern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db33392deb16664e48c3b2d90df883294d5cfbaa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441162"
---
# <a name="outlining"></a>Gliedern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können festlegen, dass bestimmter Code in der Ansicht ausgeblendet wird, indem Sie einen Codebereich reduzieren, der dann unterhalb eines Pluszeichens (+) angezeigt wird. Sie erweitern einen reduzierten Bereich, indem Sie auf das Pluszeichen klicken. (Alternativ können Sie STRG+M+M drücken, um einen Bereich zu reduzieren, und dann STRG+M+M drücken, um ihn wieder zu erweitern.) Sie können einen Gliederungsbereich auch reduzieren, indem Sie am Gliederungsrand auf eine beliebige Zeile im Bereich doppelklicken, der direkt auf der linken Seite des Codes angezeigt. Sie können den Inhalt eines reduzierten Bereichs als QuickInfo sehen, wenn Sie auf den reduzierten Bereich zeigen.  
  
 Bereiche am Gliederungsrand werden auch hervorgehoben, wenn Sie mit der Maus auf den Rand zeigen. Die standardmäßige Hervorhebungsfarbe wird möglicherweise in einigen Farbkonfigurationen etwas schwach angezeigt. Sie können sie unter **Extras/Optionen/Umgebung/Schriftarten und Farben/Zuklappbarer Bereich** ändern.  
  
 Wenn Sie mit Code mit Rand arbeiten, können Sie die Bereiche erweitern, an denen Sie arbeiten, sie reduzieren, wenn Sie fertig sind, und dann mit anderen Bereichen fortfahren. Wenn Sie die Gliederung nicht anzeigen möchten, können Sie mit dem Befehl **Gliederung entfernen** die Gliederungsinformationen entfernen, ohne damit zugrunde liegenden Code zu beeinträchtigen.  
  
 Diese Aktionen werden durch die Befehle **Rückgängig** und **Wiederholen** im Menü **Bearbeiten** beeinflusst. Bei den Befehlen **Kopieren**, **Ausschneiden** und **Einfügen** sowie bei Drag & Drop-Vorgängen werden Gliederungsinformationen beibehalten, der Zustand des zuklappbaren Bereichs jedoch nicht. Wenn Sie beispielsweise einen zugeklappten Bereich kopieren, wird der kopierte Text beim Vorgang **Einfügen** als aufgeklappter Bereich eingefügt.  
  
> [!CAUTION]
> Wenn Sie einen gegliederten Bereich ändern, geht die Gliederung möglicherweise verloren. Beispielsweise wird durch Löschvorgänge oder Suchen und Ersetzen das Ende des Bereichs möglicherweise gelöscht.  
  
 Die folgenden Befehle sind im Untermenü **Bearbeiten/Gliedern** zu finden:  
  
|||  
|-|-|  
|Aktuelles Element umschalten|(STRG+M, STRG+H) – Reduziert einen ausgewählten Codeblock, der normalerweise nicht für eine Gliederung verfügbar wäre, beispielsweise einen `if`-Block. Um den benutzerdefinierten Bereich zu entfernen, verwenden Sie **Gliederung in aktuellem Element entfernen** (oder STRG+M, STRG+U). Nicht in Visual Basic verfügbar.|  
|Gliederungserweiterung umschalten|- Kehrt den aktuellen Zustand (ausgeblendet oder erweitert) des innersten Gliederungsbereichs um, wenn sich der Cursor in einem verschachtelten reduzierten Bereich befindet.|  
|Alle Gliederungen umschalten|(STRG+M, STRG+L) – Legt alle Bereiche auf denselben reduzierten oder erweiterten Zustand fest. Wenn einige Bereiche erweitert und andere reduziert sind, werden die reduzierten Bereiche erweitert.|  
|Gliederung entfernen|(STRG+M, STRG+P) – Entfernt alle Gliederungsinformationen für das gesamte Dokument.|  
|Gliederung in aktuellem Element entfernen|(STRG+M, STRG+U) – Entfernt die Gliederungsinformationen für den aktuell ausgewählten benutzerdefinierten Bereich. Nicht in Visual Basic verfügbar.|  
|Nur Definitionen anzeigen|(STRG+M, STRG+O) – Reduziert die Member aller Typen.|  
|Block zuklappen:\<logische Begrenzung>|(Visual C++) Reduziert einen Bereich in der Funktion mit der Einfügemarke. Wenn beispielsweise die Einfügemarke innerhalb einer Schleife platziert ist, wird die Schleife ausgeblendet.|  
|Alle zuklappen in: \<logische Strukturen>|(Visual C++) Reduziert alle Strukturen innerhalb der Funktion.|  
  
 Sie können auch das Visual Studio SDK verwenden, um die Textbereiche zu definieren, die Sie erweitern oder reduzieren möchten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md).
