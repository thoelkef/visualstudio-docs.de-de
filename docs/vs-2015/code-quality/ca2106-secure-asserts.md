---
title: 'CA2106: Sichere Assert-Vorgänge | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6ca37a7bdcad290f9ab0c6d54814615731f6678c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864730"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Sichere Bestätigungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt.

## <a name="rule-description"></a>Regelbeschreibung
 Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. Ein Sicherheitsstackwalk wird beendet, wenn eine Sicherheitsberechtigung gewährt wird. Wenn Sie eine Berechtigung ohne jegliche Überprüfung des Aufrufers gewähren, kann der Aufrufer indirekt Code ausführen, mithilfe Ihrer Berechtigungen. Assert-Vorgänge ohne sicherheitsüberprüfungen zulässig sind, nur wenn Sie sicher sind, dass die Assertion auf schädliche Weise verwendet werden kann. Assert ist harmlos, wenn der Code, den Sie aufrufen, harmlos ist oder Benutzer können willkürlichen Informationen an Code, den Sie aufrufen übergeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Methode oder der deklarierende Typ eine sicherheitsforderung hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer sorgfältigen sicherheitsreview.

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Richtlinien Schreiben von sicherem Code](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)



