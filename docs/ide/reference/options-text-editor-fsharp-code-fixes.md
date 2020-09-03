---
title: Optionen, Text-Editor, F#, Codekorrekturen
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770935"
---
# <a name="options-text-editor--f--code-fixes"></a>Optionen: Text-Editor > F# > Codekorrekturen

Verwenden Sie die Optionenseite „Codekorrekturen“, um die Einstellungen festzulegen, mit denen Sie Codefehler identifizieren und Lösungen anbieten können. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Tools** > **Optionen** und anschließend auf **Text-Editor** > **F#**  > **Codekorrekturen**.

## <a name="code-fixes"></a>Codekorrekturen

- **Namen vereinfachen (Unnötige Qualifizierer entfernen)**

  Wenn dieses Kontrollkästchen aktiviert ist, werden voll qualifizierte Namen vereinfacht, wenn die Qualifizierer nicht erforderlich sind, z.B. für ein Mitglied eines häufig verwendeten Namespaces.

- **Offenen Anweisungen immer auf der obersten Ebene platzieren**

  Wenn dieses Kontrollkästchen aktiviert ist und Sie eine `open`-Anweisung in den Code eingeben, wird sie auf der obersten Ebene platziert.

- **Nicht verwendete offene Anweisungen entfernen**

  Wenn dieses Kontrollkästchen aktiviert ist, werden Dokumente auf unbenutzte `open`-Anweisungen analysiert, und es wird ein Glühbirnensymbol für eine [Schnelle Aktion](../quick-actions.md) mit einer Aktion zum Entfernen aller unbenutzten `open`-Anweisungen angezeigt.

- **Analysieren und Lösungen für nicht verwendete Werte vorschlagen**

  Wenn dieses Kontrollkästchen aktiviert ist, erkennt das Tool einen Wert, der nicht im Code verwendet wird. Wenn Sie dann mit der Maus über den unbenutzten Wert fahren, wird empfohlen, wie Sie den Wert verwenden können.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Ermitteln von Änderungen am Code und anderer Verläufe mit CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
