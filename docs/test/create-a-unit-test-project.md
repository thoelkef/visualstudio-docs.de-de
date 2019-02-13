---
title: Ein Komponententestprojekt erstellen
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 381f04b78e5cfc9ed61187e62e310a2d927eb0ce
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949433"
---
# <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen

Komponententests spiegeln häufig die Struktur des getesteten Codes. Angenommen, für jedes Codeprojekt im Produkt wird ein Komponententestprojekt erstellt. Das Testprojekt kann sich in der gleichen Projektmappe wie der Produktionscode oder in einer separaten Projektmappe befinden. In einer Projektmappe können sich mehrere Komponententestprojekte befinden.

> [!NOTE]
> Der Speicherort von Komponententests für nativen Code und die Testprojektstruktur können sich von in diesem Artikel beschriebenen Struktur unterscheiden. Weitere Informationen finden unter [Erstellen von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Komponententestprojekt

1. Wählen Sie im Menü **Datei** die Option **Neu** und anschließend **Projekt** aus. Drücken Sie alternativ auf **STRG**+**UMSCHALT**+**N**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Installiert**, wählen die Sprache aus, die Sie für das Testprojekt verwenden möchten, und wählen Sie anschließend **Test** aus.

3. Wenn Sie ein Microsoft-Komponententest-Framework verwenden möchten, wählen Sie aus der Liste der Projektvorlagen **Komponententestprojekt** aus. Wählen Sie andernfalls die Projektvorlage des Komponententest-Frameworks aus, das Sie verwenden möchten. Geben Sie dem Projekt einen Namen, und klicken Sie dann auf **OK**.

4. Fügen Sie Ihrem Komponententestprojekt einen Verweis auf den zu testenden Code hinzu. So fügen Sie einen Verweis auf ein Codeprojekt in derselben Projektmappe ein:

   1. Wählen Sie das Testprojekt im **Projektmappen-Explorer** aus.

   2. Wählen Sie im Menü **Projekt** den Eintrag **Verweis hinzufügen**aus.

   3. Wählen Sie im **Verweis-Manager** den Knoten **Projektmappe** unter **Projekte** aus. Wählen Sie das zu testende Codeprojekt aus, und klicken Sie dann auf **OK**.

   Wenn sich der zu testende Code an einem anderen Speicherort befindet, finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md) weitere Informationen zum Hinzufügen eines Verweises.

## <a name="next-steps"></a>Nächste Schritte

Siehe eines der folgenden Themen:

**Schreiben von Komponententests**

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

- [Verwenden des MSTest-Frameworks in Komponententests](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Ausführen von Komponententests**

- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)