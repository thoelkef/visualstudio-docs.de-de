---
title: Formatierung, XML, Text-Editor, Dialog Feld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670974"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatierung, XML, Texteditor, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML-Editor angeben. Sie können **im Menü Extras auf das Dialog** Feld **Optionen** zugreifen.

> [!NOTE]
> Diese Einstellungen sind verfügbar, wenn Sie den Ordner " **Text-Editor** ", den Ordner " **XML** " und dann im Dialogfeld " **Optionen** " die Option **Formatierung** auswählen.

## <a name="attributes"></a>Attribute
 **Manuelle Attribut Formatierung beibehalten** Attribute werden nicht neu formatiert. Dies ist die Standardeinstellung.

> [!NOTE]
> Wenn sich die Attribute auf mehreren Zeilen befinden, zieht der Editor jede Attributzeile ein, sodass das Einzugsmuster des übergeordneten Elements festgelegt wird.

 **Attribute jeweils in einer eigenen Zeile ausrichten** Richtet das zweite und die nachfolgenden Attribute vertikal aus, sodass Sie dem Einzug des ersten Attributs entsprechen. Der folgende XML-Text veranschaulicht, wie die Attribute ausgerichtet werden.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatisch neu formatieren
 **Beim Einfügen aus der Zwischenablage** Formatiert den aus der Zwischenablage eingefügten XML-Text neu.

 **Beim Abschluss des Endtags** Formatiert das Element neu, wenn das Endtag abgeschlossen ist.

## <a name="mixed-content"></a>Gemischter Inhalt
 **Gemischten Inhalt standardmäßig beibehalten** Bestimmt, ob der Editor gemischte Inhalte neu formatiert. Der Editor versucht standardmäßig, gemischten Inhalt neu zu formatieren, es sei denn, der Inhalt befindet sich in einem `xml:space="preserve"`-Gültigkeitsbereich.

 Wenn ein Element eine Mischung aus Text und Markup enthält, wird der Inhalt als gemischter Inhalt betrachtet. Es folgt als Beispiel ein Element mit gemischtem Inhalt.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Siehe auch
 [XML-Dokumenteigenschaften, Eigenschaften Fenster](../xml-tools/xml-document-properties-properties-window.md) - [XML-Editor-Komponenten](../xml-tools/xml-editor-components.md)
