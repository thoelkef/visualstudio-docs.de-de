---
title: Verfügbar machen Listen von Symbolen, die dem Objekt-Manager bereitgestellt werden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsSimpleLibrary2 interface, lists of symbols
- IVsLibrary2 interface, lists of symbols
- symbols, call browser
- lists, symbols for the object manager
- symbols, exposing lists to the object manager
ms.assetid: 19757068-bdaa-4e7e-85d6-f8ce5026a859
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb15b7d9b29c578a0acf43fd1aa9cfdea88e23ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708085"
---
# <a name="how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager"></a>Gewusst wie: Listen von Symbolen verfügbar machen, die von der Bibliothek für den Objektmanager bereitgestellt werden
Die Symbol-Browsing-Tools, **Class View**, **Object Browser**, Call **Browser** und Find **Symbol Results**, übergeben Anforderungen für neue Daten an den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager. Der Objekt-Manager findet die entsprechenden Bibliotheken und fordert neue Symbollisten an. Die Bibliotheken reagieren, indem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sie dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Objekt-Manager über die Schnittstelle angeforderte Daten zur Verfügung stellen. Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> die Methoden in der Schnittstelle auf, um die Daten abzuerhalten, und verwendet sie, um die Ansichten der Symbol-Browsing-Tools aufzufüllen oder zu aktualisieren.

 Eine Bibliothek kann Datenanforderungen abrufen, wenn das Tool aufgerufen, der Knoten erweitert oder die Ansicht aktualisiert wird. Wenn ein Symbol-Browsing-Tool zum ersten Mal aufgerufen wird, fordert der Objekt-Manager die Bibliothek auf, die Liste der obersten Ebene bereitzustellen. Wenn der Benutzer einen Listenknoten erweitert, stellt die Bibliothek eine Liste der untergeordneten Elemente unter diesem Knoten bereit. Jede Objektmanagerabfrage enthält einen Index des Interessenten. Um eine neue Liste anzuzeigen, muss der Objekt-Manager bestimmen, wie viele Elemente in der Liste enthalten sind, wie die Elemente, ihre Namen, ihre Zugänglichkeit und andere Eigenschaften sind.

> [!NOTE]
> Die folgenden Beispiele für verwalteten Code veranschaulichen, wie Sie Listen von Symbolen durch implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Schnittstelle bereitstellen. Der Objekt-Manager ruft die Methoden in dieser Schnittstelle auf und verwendet die erhaltenen Daten, um die Symbol-Browsing-Tools aufzufüllen oder zu aktualisieren.
>
> Verwenden Sie für die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> des systemeigenen Codesymbolanbieters die Schnittstelle.

## <a name="to-provide-lists-of-symbols-to-the-object-manager"></a>So stellen Sie Dem Objekt-Manager Symbollisten zur Verfügung

1. Abrufen der Anzahl der Elemente in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> Liste der Symbole durch Implementieren der Methode. Im folgenden Beispiel wird veranschaulicht, wie der Objekt-Manager die Informationen zur Anzahl der Elemente in der Liste abruft.

    ```vb
    Protected m_Methods As System.Collections.Generic.SortedList(Of String, Method) = New System.Collections.Generic.SortedList(Of String, Method)()

    Public Function GetItemCount(ByRef pCount As UInteger) As Integer
        pCount = CUInt(m_Methods.Count)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    protected System.Collections.Generic.SortedList<string, Method> m_Methods = new System.Collections.Generic.SortedList<string, Method>();

    public int GetItemCount(out uint pCount)
    {
        pCount = (uint)m_Methods.Count;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

2. Durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> Methode erhalten Sie Informationen zu den Kategorien und Attributen eines bestimmten Listenelements. Die Elementkategorien werden <xref:Microsoft.VisualStudio.Shell.Interop.LIB_CATEGORY> in der Enumeration angegeben. Im folgenden Beispiel wird veranschaulicht, wie der Objekt-Manager Attribute von Elementen für eine bestimmte Kategorie abruft.

    ```vb
    Public Function GetCategoryField2(ByVal index As UInteger, ByVal Category As Integer, ByRef pfCatField As UInteger) As Integer
        pfCatField = 0

        Select Case CType(Category, LIB_CATEGORY)
            Case LIB_CATEGORY.LC_MEMBERTYPE
                pfCatField = CUInt(_LIBCAT_MEMBERTYPE.LCMT_METHOD)

            Case LIB_CATEGORY.LC_MEMBERACCESS
                Dim method As Method = m_Methods.Values(CInt(Fix(index)))

                If method.IsPublic Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PUBLIC)
                ElseIf method.IsPrivate Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PRIVATE)
                ElseIf method.IsFamily Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED)
                ElseIf method.IsFamilyOrAssembly Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED) Or CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                Else
                    ' Show everything else as internal.
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                End If

            Case LIB_CATEGORY.LC_VISIBILITY
                pfCatField = CUInt(_LIBCAT_VISIBILITY.LCV_VISIBLE)

            Case LIB_CATEGORY.LC_LISTTYPE
                pfCatField = CUInt(_LIB_LISTTYPE.LLT_MEMBERS)

            Case Else
                Return Microsoft.VisualStudio.VSConstants.S_FALSE
        End Select
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetCategoryField2(uint index, int Category, out uint pfCatField)
    {
        pfCatField = 0;

        switch ((LIB_CATEGORY)Category)
        {
            case LIB_CATEGORY.LC_MEMBERTYPE:
                pfCatField = (uint)_LIBCAT_MEMBERTYPE.LCMT_METHOD;
                break;

            case LIB_CATEGORY.LC_MEMBERACCESS:
                {
                    Method method = m_Methods.Values[(int)index];

                    if (method.IsPublic)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PUBLIC;
                    }
                    else if (method.IsPrivate)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PRIVATE;
                    }
                    else if (method.IsFamily)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED;
                    }
                    else if (method.IsFamilyOrAssembly)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED |
                                     (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                    else
                    {
                        // Show everything else as internal.
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                }
                break;

            case LIB_CATEGORY.LC_VISIBILITY:
                pfCatField = (uint)_LIBCAT_VISIBILITY.LCV_VISIBLE;
                break;

            case LIB_CATEGORY.LC_LISTTYPE:
                pfCatField = (uint)_LIB_LISTTYPE.LLT_MEMBERS;
                break;

            default:
                return Microsoft.VisualStudio.VSConstants.S_FALSE;
        }
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

3. Abrufen der Textdarstellung eines bestimmten Listenelements durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> Methode. Im folgenden Beispiel wird veranschaulicht, wie Sie einen vollständigen Namen eines bestimmten Elements abrufen.

    ```vb
    Public Function GetTextWithOwnership(<System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")> ByVal index As UInteger, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")> ByVal tto As Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")> ByRef ppszText As String) As Integer
        ppszText = m_Methods.Values(CInt(Fix(index))).FullName
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetTextWithOwnership([System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")] uint index, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")] Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS tto, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")] out string ppszText)
    {
        ppszText = m_Methods.Values[(int)index].FullName;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

4. Abrufen der Symbolinformationen für ein bestimmtes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> Listenelement durch Implementieren der Methode. Das Symbol stellt den Typ (Klasse, Methode usw.) und Die Barrierefreiheit (privat, öffentlich usw.) eines Listenelements dar. Im folgenden Beispiel wird veranschaulicht, wie die Symbolinformationen basierend auf einem bestimmten Elementattribut abrufst.

    ```vb
    Public Overridable Function GetDisplayData(ByVal index As UInteger, ByVal pData As Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA()) As Integer
        If pData Is Nothing Then
            Return Microsoft.VisualStudio.VSConstants.E_INVALIDARG
        End If

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))

        Dim iImage As Integer = 12 * 6 ' See env\inc\OMGlyphs.h.

        Const OM_GLYPH_ACC_PUBLIC As Integer = 0
        Const OM_GLYPH_ACC_INTERNAL As Integer = 1
        Const OM_GLYPH_ACC_PROTECTED As Integer = 3
        Const OM_GLYPH_ACC_PRIVATE As Integer = 4

        If method.IsPublic Then
            iImage += OM_GLYPH_ACC_PUBLIC
        ElseIf method.IsPrivate Then
            iImage += OM_GLYPH_ACC_PRIVATE
        ElseIf method.IsFamily Then
            iImage += OM_GLYPH_ACC_PROTECTED
        ElseIf method.IsFamilyOrAssembly Then
            iImage += OM_GLYPH_ACC_PROTECTED
        Else
            iImage += OM_GLYPH_ACC_INTERNAL
        End If

        pData(0).Image = CUShort(iImage)
        pData(0).SelectedImage = CUShort(iImage)

        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public virtual int GetDisplayData(uint index, Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA[] pData)
    {
        if (pData == null)
        {
            return Microsoft.VisualStudio.VSConstants.E_INVALIDARG;
        }

        Method method = m_Methods.Values[(int)index];

        int iImage = 12 * 6;    // See env\inc\OMGlyphs.h.

        const int OM_GLYPH_ACC_PUBLIC = 0;
        const int OM_GLYPH_ACC_INTERNAL = 1;
        const int OM_GLYPH_ACC_PROTECTED = 3;
        const int OM_GLYPH_ACC_PRIVATE = 4;

        if (method.IsPublic)
        {
            iImage += OM_GLYPH_ACC_PUBLIC;
        }
        else if (method.IsPrivate)
        {
            iImage += OM_GLYPH_ACC_PRIVATE;
        }
        else if (method.IsFamily)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else if (method.IsFamilyOrAssembly)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else
        {
            iImage += OM_GLYPH_ACC_INTERNAL;
        }

        pData[0].Image = (ushort)iImage;
        pData[0].SelectedImage = (ushort)iImage;

        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

5. Hier erhalten Sie Informationen darüber, ob ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> bestimmtes Listenelement durch Implementieren der Methode erweiterbar ist. Im folgenden Beispiel wird veranschaulicht, wie Sie Informationen darüber abrufen, ob ein bestimmtes Element erweitert werden kann.

    ```vb
    Public Function GetExpandable(ByVal index As UInteger, ByRef pfExpandable As Integer) As Integer
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    Public Function GetExpandable3(ByVal index As UInteger, ByVal ListTypeExcluded As UInteger, ByRef pfExpandable As Integer) As Integer
        Return GetExpandable(index, pfExpandable)
    End Function
    ```

    ```csharp
    public int GetExpandable(uint index, out int pfExpandable)
    {
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    public int GetExpandable3(uint index, uint ListTypeExcluded, out int pfExpandable)
    {
        return GetExpandable(index, out pfExpandable);
    }

    ```

6. Abrufen einer untergeordneten Liste von Symbolen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> eines bestimmten Listenelements durch Implementieren der Methode. Im folgenden Beispiel wird veranschaulicht, wie Sie eine untergeordnete Liste von Symbolen eines bestimmten Elements für **Anruf-** oder **Anruferdiagramme** abrufen.

    ```vb
    ' Call graph list.
    Public Class CallsList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallsList(index, ppList)
        End Function
    End Class

    ' Callers graph list.
    Public Class CallersList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallersList(index, ppList)
        End Function
    End Class

    ' Call graph list.
    Public Function GetCallsList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callsList As ResultsList = New CallsList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Calls As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallGraph(method)

        For i As Integer = 0 To Calls.Count - 1
            Dim caller As Method = Calls(i).m_Target
            callsList.AddMethod(caller)
        Next i

        ppList = CType(callsList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Callers graph list.
    Public Function GetCallersList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callersList As ResultsList = New CallersList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Callers As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallersGraph(method)

        For i As Integer = 0 To Callers.Count - 1
            Dim caller As Method = Callers(i).m_Source
            callersList.AddMethod(caller)
        Next i

        ppList = CType(callersList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Get a child list of symbols for a given list item.
    Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        ' Determine if the list belongs to Call or Callers graphs.
        If CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM)) > 0 Then
            ' Build the list for the Call graph.
            Return MyBase.GetCallsList(index, ppList)
        ElseIf CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO)) > 0 Then
            ' Build the list for the Callers graph.
            Return MyBase.GetCallersList(index, ppList)
        End If

        Return Microsoft.VisualStudio.VSConstants.E_FAIL
    End Function
    ```

    ```csharp
    // Call graph list.
    public class CallsList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallsList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallsList(index, out ppList);
        }
    }

    // Callers graph list.
    public class CallersList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallersList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallersList(index, out ppList);
        }
    }

    // Call graph list.
    public int GetCallsList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callsList = new CallsList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Calls = m_Library.CallGraph.GetCallGraph(method);

        for (int i = 0; i < Calls.Count; i++)
        {
            Method caller = Calls[i].m_Target;
            callsList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callsList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Callers graph list.
    public int GetCallersList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callersList = new CallersList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Callers = m_Library.CallGraph.GetCallersGraph(method);

        for (int i = 0; i < Callers.Count; i++)
        {
            Method caller = Callers[i].m_Source;
            callersList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callersList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Get a child list of symbols for a given list item.
    public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        // Determine if the list belongs to Call or Callers graphs.
        if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM) > 0)
        {
            // Build the list for the Call graph.
            return base.GetCallsList(index, out ppList);
        }
        else if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO) > 0)
        {
            // Build the list for the Callers graph.
            return base.GetCallersList(index, out ppList);
        }

        return Microsoft.VisualStudio.VSConstants.E_FAIL;
    }

    ```

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung von Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Gewusst wie: Registrieren einer Bibliothek beim Objektmanager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Gewusst wie: Identifizieren von Symbolen in einer Bibliothek](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
- [Erweiterbarkeit des Legacy-Sprachdienstes](../../extensibility/internals/legacy-language-service-extensibility.md)
