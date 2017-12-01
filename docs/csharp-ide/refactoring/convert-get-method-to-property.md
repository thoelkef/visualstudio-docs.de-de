---
title: Konvertieren von Get-Methode, Eigenschaft - Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Konvertieren von Get-Methode, Eigenschaft / Eigenschaft umwandeln, um Get-Methode
## <a name="convert-get-method-to-property"></a>Konvertieren von Get-Methode, Eigenschaft
**Was:** können Sie eine Get-Methode in einer Eigenschaft (und optional die Set-Methode) zu konvertieren und umgekehrt.

**Wann:** Sie verwenden eine Get-Methode, die keine Logik enthalten.

**Vorgehensweise:**

1. Platzieren Sie den Cursor in die Namen der Get-Methode.

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Replace-Methode mit der Eigenschaft** im Popupmenü Fenster Vorschau. Wenn Sie eine Set-Methode verfügen, können Sie auch die Set-Methode zu diesem Zeitpunkt konvertieren, dazu **Methode ersetzen Get und Set-Methode, mit der Eigenschaft**.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** Menü **Replace-Methode mit der Eigenschaft** im Popupmenü Fenster Vorschau. Wenn Sie eine Set-Methode verfügen, können Sie auch die Set-Methode zu diesem Zeitpunkt konvertieren, dazu **Methode ersetzen Get und Set-Methode, mit der Eigenschaft**.

1. Wenn Sie mit der Änderung in der Codevorschau zufrieden sind, drücken Sie **EINGABETASTE** oder klicken Sie auf das Update aus dem Menü, und die Änderungen werden ein Commit ausgeführt werden.

Beispiel:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Konvertieren Sie die Eigenschaft in Get-Methode
**Was:** können Sie die Konvertierung einer Eigenschaft in einer Get-Methode

**Wann:** stehen Ihnen eine Eigenschaft, die mehr als sofort festlegen und Abrufen eines Werts umfasst 

**Vorgehensweise:**

1. Platzieren Sie den Cursor in die Namen der Get-Methode.

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Methoden Eigenschaft ersetzt** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** Menü **Methoden Eigenschaft ersetzt** im Popupmenü Fenster Vorschau.

1. Wenn Sie mit der Änderung in der Codevorschau zufrieden sind, drücken Sie **EINGABETASTE** oder klicken Sie auf das Update aus dem Menü, und die Änderungen werden ein Commit ausgeführt werden.

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)