---
title: Ein Komponententestprojekt erstellen
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f04e999681899bb101dc0aeb70cc6f47094dc1d7
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483827"
---
# <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen

Komponententests spiegeln häufig die Struktur des getesteten Codes. Angenommen, für jedes Codeprojekt im Produkt wird ein Komponententestprojekt erstellt. Das Testprojekt kann sich in der gleichen Projektmappe wie der Produktionscode oder in einer separaten Projektmappe befinden. In einer Projektmappe können sich mehrere Komponententestprojekte befinden.

> [!NOTE]
> Der Speicherort von Komponententests für nativen Code und die Testprojektstruktur können sich von in diesem Artikel beschriebenen Struktur unterscheiden. Weitere Informationen finden unter [Erstellen von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>So erstellen Sie ein Komponententestprojekt

1. Wählen Sie im Menü **Datei** die Befehlsfolge **Neu** > **Projekt...** aus, oder drücken Sie **STRG**+**UMSCHALT**+**N**.

::: moniker range="vs-2017"

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Installiert**, wählen die Sprache aus, die Sie für das Testprojekt verwenden möchten, und wählen Sie anschließend **Test** aus.

3. Wählen Sie die Projektvorlage für das Testframework aus, das Sie verwenden möchten, z. B. **MSTest Test Project** oder **NUnit Test Project**. Geben Sie dem Projekt einen Namen, und klicken Sie dann auf **OK**.

   ![Testprojektvorlagen in Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie auf der Seite **Neues Projekt erstellen** **Komponententest** in das Suchfeld ein. Wählen Sie die Projektvorlage für das Testframework aus, das Sie verwenden möchten, z. B. **MSTest Test Project** oder **NUnit Test Project**, und klicken Sie auf **Weiter**.

   ![Testprojektvorlagen in Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Geben Sie auf der Seite **Neues Projekt konfigurieren** einen Namen für Ihr Projekt ein, und klicken Sie dann auf **Erstellen**.

::: moniker-end

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