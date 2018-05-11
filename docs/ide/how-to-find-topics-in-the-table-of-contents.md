---
title: Verwenden des Inhaltsverzeichnisses von Visual Studio Help Viewer
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e7d9ae19cb2a37c6fbf6595a7f3a39895d22190
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Vorgehensweise: Suchen nach Themen im Inhaltsverzeichnis

Auf der Registerkarte **Inhalt** können Sie das Inhaltsverzeichnis verwenden, um Informationen zu suchen. Das Inhaltsverzeichnis ist eine erweiterbare Liste, die alle Themen in den installierten Büchern enthält. Informationen zur Navigation durch das Inhaltsverzeichnis mithilfe von Tastenkombinationen finden Sie unter [Tastenkombinationen (Help Viewer)](../ide/shortcut-keys-help-viewer.md).

> [!IMPORTANT]
> Der Themenbereich, der im Inhaltsverzeichnis verfügbar ist, ist vom ausgewählten Filter abhängig.

## <a name="filter-the-toc"></a>Filtern des Inhaltsverzeichnisses

Sie können das Inhaltsverzeichnis filtern, um den Themenbereich einzugrenzen, der auf der Registerkarte **Inhalt** angezeigt wird. Titel werden nur in der Liste angezeigt, wenn sie den Stamm des angegebenen Begriffs enthalten. Wenn Sie beispielsweise "Problembehandlung" als Filter angeben, werden nur Titel angezeigt, die "Problem" oder "Problembehandlung" enthalten. Knoten, deren Namen nicht den Begriff enthalten, werden auf einem einzelnen Knoten mit Auslassungszeichen (**...**) reduziert.

1.  Klicken Sie auf die Registerkarte **Inhalt**.

2.  Geben Sie im Textfeld **Inhalte filtern** einen Begriff ein.

> [!NOTE]
> Wenn die Ausführung des Filters viel Zeit in Anspruch nimmt, versuchen Sie es mit dem erweiterten Suchoperator `title:`, wodurch Ergebnisse möglicherweise schneller angezeigt werden.

## <a name="synchronize-a-topic-with-the-toc"></a>Synchronisieren von Themen mit dem Inhaltsverzeichnis

Wenn Sie ein Thema mithilfe der Index- oder Volltextsuchfunktionen geöffnet haben, können Sie bestimmen, wo dieses Thema im Inhaltsverzeichnis angezeigt wird, indem Sie das Inhaltsverzeichnis mit dem Themenfenster synchronisieren.

1.  Zeigen Sie ein Thema an.

2.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Thema in Inhalten anzeigen**, oder drücken Sie **STRG+**+**S**.

     Die Registerkarte **Inhalt** wird geöffnet und zeigt den Speicherort des Themas im Inhaltsverzeichnis an.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Suchen von Themen im Index](../ide/how-to-find-topics-in-the-index.md)
- [Vorgehensweise: Suchen nach Themen](../ide/how-to-search-for-topics.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)