---
title: Ein Komponententestprojekt erstellen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e90aa1f8fe13bc7ee99f3ac20b1813ca2a6c9672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996813"
---
# <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen

Komponententests spiegeln häufig die Struktur des getesteten Codes. Angenommen, für jedes Codeprojekt im Produkt wird ein Komponententestprojekt erstellt. Das Testprojekt kann sich in der gleichen Projektmappe wie der Produktionscode oder in einer separaten Projektmappe befinden. In einer Projektmappe können sich mehrere Komponententestprojekte befinden.

> [!NOTE]
> Der Speicherort von Komponententests für nativen Code und die Testprojektstruktur können sich von in diesem Thema beschriebenen Struktur unterscheiden. Weitere Informationen finden unter [Erstellen von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Komponententestprojekt

1.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt** (Tastatur: **STRG**+**UMSCHALTTASTE**+**N**).

2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Installiert**, wählen die Sprache aus, die Sie für das Testprojekt verwenden möchten, und wählen Sie anschließend **Test** aus.

3.  Wenn Sie ein Microsoft-Komponententest-Framework verwenden möchten, wählen Sie aus der Liste der Projektvorlagen **Komponententestprojekt** aus. Wählen Sie andernfalls die Projektvorlage des Komponententest-Frameworks aus, das Sie verwenden möchten. Nennen Sie das Projekt zum Testen des Projekts „Accounts“ in diesem Beispiel **AccountsTests**.

4.  Fügen Sie Ihrem Komponententestprojekt einen Verweis auf den zu testenden Code hinzu.  So erstellen Sie den Verweis auf ein Codeprojekt in der gleichen Projektmappe:

    1.  Wählen Sie das Projekt im **Projektmappen-Explorer** aus.

    2.  Wählen Sie im Menü **Projekt** den Eintrag **Verweis hinzufügen**aus.

    3.  Öffnen Sie im Dialogfeld **Verweis-Manager** den Knoten **Projektmappe**, und wählen Sie **Projekte** aus. Wählen Sie den Namen des Codeprojekts aus, und schließen Sie das Dialogfeld.

5.  Wenn sich der zu testende Code an einem anderen Speicherort befindet, finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md) weitere Informationen zum Hinzufügen von Verweisen.

## <a name="next-steps"></a>Nächste Schritte

 Siehe eines der folgenden Themen:

**Schreiben von Komponententests**

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

- [Verwenden des MSTest-Frameworks in Komponententests](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Ausführen von Komponententests**

- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)