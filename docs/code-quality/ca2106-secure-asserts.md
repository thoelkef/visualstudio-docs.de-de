---
title: "CA2106: Sichere bestätigt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 321d00f13ebc891070549778239fec60201d03c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2106-secure-asserts"></a>CA2106: Sichere Bestätigungen
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. Ein Sicherheits-Stackwalk beendet, wenn eine Sicherheitsberechtigung übergeben wird. Wenn Sie eine Berechtigung gewähren, ohne jegliche Überprüfung des Aufrufers, könnte der Aufrufer indirekt Code ausführen, mit Ihren Berechtigungen. Bestätigt, ohne sicherheitsüberprüfungen zulässig sind, nur wenn Sie sicher sind, dass die Assertion auf schädliche Weise verwendet werden kann. Eine Assertion ist ignorieren, wenn der Code, den Sie aufrufen harmlos ist, oder Benutzer können beliebigen Informationen an Code, den Sie aufrufen übergeben.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine sicherheitsforderung auf die Methode oder der deklarierende Typ hinzu.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer sorgfältigen sicherheitsreview.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)