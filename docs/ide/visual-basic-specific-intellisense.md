---
title: Visual Basic IntelliSense | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44ff32ed0452efb5e413d730a69293147fec4c7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense für Visual Basic-Codedateien

Der Quellcode-Editor von Visual Basic stellt die folgenden IntelliSense-Features bereit:

## <a name="syntax-tips"></a>Tipps zur Syntax

In den Tipps zur Syntax wird die Syntax der Anweisung angezeigt, die Sie eintippen. Dies ist für Anweisungen wie [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) nützlich.

## <a name="automatic-completion"></a>Automatische Vervollständigung

- Vervollständigung unterschiedlicher Schlüsselwörter

     Wenn Sie beispielsweise `goto` und ein Leerzeichen eingeben, zeigt IntelliSense eine Liste der definierten Bezeichnungen in einem Dropdownmenü. Andere unterstützte Schlüsselwörter sind unter anderem `Exit`, `Implements`, `Option` und `Declare`.

- Vervollständigung für `Enum` und `Boolean`

    Wenn eine Anweisung auf einen Member einer Enumeration verweist, zeigt IntelliSense eine Liste der Members der `Enum`-Aufzählung. Wenn eine Anweisung auf `Boolean` verweist, zeigt IntelliSense ein Dropdownmenü mit TRUE und FALSE an.

Die Vervollständigung kann standardmäßig deaktiviert werden. Wählen Sie hierzu von der Eigenschaftenseite **Allgemein** im Ordner **Visual Basic** **Member automatisch auflisten** aus.

Sie können die Vervollständigung manuell aufrufen, indem Sie auf „Member auflisten“ oder „Wort vervollständigen“ klicken oder ALT+NACH-RECHTS-TASTE drücken. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense pro Zone

„IntelliSense pro Zone“ hilft Visual Basic-Entwicklern, die Anwendungen über [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellen müssen und durch Einstellungen für teilweise vertrauenswürdige Anwendungen eingeschränkt sind. Mithilfe dieser Funktion

- wird Ihnen ermöglicht, die Berechtigungen auszuwählen, mit der die Anwendung ausgeführt wird.

- werden APIs in der ausgewählten Zone in „Member auflisten“ als verfügbar angezeigt und APIs, die zusätzliche Berechtigungen erfordern, als nicht verfügbar angezeigt.

Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Gefilterte Vervollständigungslisten

In Visual Basic verfügen IntelliSense-Vervollständigungslisten über zwei Registersteuerelemente, die sich am unteren Rand der Liste befinden. Die Registerkarte **Allgemein**, die standardmäßig ausgewählt ist, zeigt Elemente, die am häufigsten zur Vervollständigung der Anweisung verwendet werden, die Sie schreiben. Die Registerkarte **Alle** zeigt alle Elemente an, die für die automatische Vervollständigung verfügbar sind, darunter auch diejenigen, die sich auch auf der Registerkarte **Allgemein** befinden.

## <a name="see-also"></a>Siehe auch

[Verwenden von IntelliSense](../ide/using-intellisense.md)