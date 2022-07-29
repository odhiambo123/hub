---
layout: post
title:  "Operator Precedence"
date:   2022-07-28 18:06
categories: JavaScript
---

<table class="fullwidth-table">
  <tbody>
    <tr>
      <th>Precedence</th>
      <th>Operator type</th>
      <th>Associativity</th>
      <th>Individual operators</th>
    </tr>
    <tr>
      <td>18 Highest</td>
      <td>
        {{jsxref("Operators/Grouping", "Grouping", "", 1)}}
      </td>
      <td>n/a</td>
      <td><code>( … )</code></td>
    </tr>
    <tr>
      <td rowspan="5">17</td>
      <td>
        {{jsxref("Operators/Property_Accessors", "Member Access", "#Dot_notation",
                1)}}
      </td>
      <td>left-to-right</td>
      <td><code>… . …</code></td>
    </tr>
    <tr>
      <td>
        {{jsxref("Operators/Property_Accessors", "Computed Member
                Access","#Bracket_notation", 1)}}
      </td>
      <td>n/a</td>
      <td><code>… [ … ]</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/new","new")}} (with argument list)</td>
      <td>n/a</td>
      <td><code>new … ( … )</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Guide/Functions">Function Call</a>
      </td>
      <td>n/a</td>
      <td>
        <code>… ( … )</code>
      </td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining"
          >Optional chaining</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>?.</code></td>
    </tr>
    <tr>
      <td>16</td>
      <td>
        {{jsxref("Operators/new","new")}} (without argument list)
      </td>
      <td>n/a</td>
      <td><code>new …</code></td>
    </tr>
    <tr>
      <td rowspan="2">15</td>
      <td>
        {{jsxref("Operators","Postfix
                Increment","#increment_and_decrement", 1)}}
      </td>
      <td rowspan="2">n/a</td>
      <td><code>… ++</code></td>
    </tr>
    <tr>
      <td>
        {{jsxref("Operators","Postfix
                Decrement","#increment_and_decrement", 1)}}
      </td>
      <td><code>… --</code></td>
    </tr>
    <tr>
      <td rowspan="10">14</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Logical_NOT"
          >Logical NOT (!)</a
        >
      </td>
      <td rowspan="10">n/a</td>
      <td><code>! …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_NOT"
          >Bitwise NOT (~)</a
        >
      </td>
      <td><code>~ …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Unary_plus"
          >Unary plus (+)</a
        >
      </td>
      <td><code>+ …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Unary_negation"
          >Unary negation (-)</a
        >
      </td>
      <td><code>- …</code></td>
    </tr>
    <tr>
      <td>
        {{jsxref("Operators","Prefix
                Increment","#increment_and_decrement", 1)}}
      </td>
      <td><code>++ …</code></td>
    </tr>
    <tr>
      <td>
        {{jsxref("Operators","Prefix
                Decrement","#increment_and_decrement", 1)}}
      </td>
      <td><code>-- …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/typeof", "typeof")}}</td>
      <td><code>typeof …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/void", "void")}}</td>
      <td><code>void …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/delete", "delete")}}</td>
      <td><code>delete …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/await", "await")}}</td>
      <td><code>await …</code></td>
    </tr>
    <tr>
      <td>13</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Exponentiation"
          >Exponentiation (**)</a
        >
      </td>
      <td>right-to-left</td>
      <td><code>… ** …</code></td>
    </tr>
    <tr>
      <td rowspan="3">12</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Multiplication"
          >Multiplication (*)</a
        >
      </td>
      <td rowspan="3">left-to-right</td>
      <td><code>… * …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Division"
          >Division (/)</a
        >
      </td>
      <td><code>… / …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Remainder"
          >Remainder (%)</a
        >
      </td>
      <td><code>… % …</code></td>
    </tr>
    <tr>
      <td rowspan="2">11</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Addition"
          >Addition (+)</a
        >
      </td>
      <td rowspan="2">left-to-right</td>
      <td><code>… + …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Subtraction"
          >Subtraction (-)</a
        >
      </td>
      <td><code>… - …</code></td>
    </tr>
    <tr>
      <td rowspan="3">10</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Left_shift"
          >Bitwise Left Shift (&#x3C;&#x3C;)</a
        >
      </td>
      <td rowspan="3">left-to-right</td>
      <td><code>… &#x3C;&#x3C; …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Right_shift"
          >Bitwise Right Shift (>>)</a
        >
      </td>
      <td><code>… >> …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift"
          >Bitwise Unsigned Right Shift (>>>)</a
        >
      </td>
      <td><code>… >>> …</code></td>
    </tr>
    <tr>
      <td rowspan="6">9</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Less_than"
          >Less Than (&#x3C;)</a
        >
      </td>
      <td rowspan="6">left-to-right</td>
      <td><code>… &#x3C; …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Less_than_or_equal"
          >Less Than Or Equal (&#x3C;=)</a
        >
      </td>
      <td><code>… &#x3C;= …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Greater_than"
          >Greater Than (>)</a
        >
      </td>
      <td><code>… > …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Greater_than_or_equal"
          >Greater Than Or Equal (>=)</a
        >
      </td>
      <td><code>… >= …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/in", "in")}}</td>
      <td><code>… in …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/instanceof", "instanceof")}}</td>
      <td><code>… instanceof …</code></td>
    </tr>
    <tr>
      <td rowspan="4">8</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Equality"
          >Equality (==)</a
        >
      </td>
      <td rowspan="4">left-to-right</td>
      <td><code>… == …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Inequality"
          >Inequality (!=)</a
        >
      </td>
      <td><code>… != …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality"
          >Strict Equality (===)</a
        >
      </td>
      <td><code>… === …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Strict_inequality"
          >Strict Inequality (!==)</a
        >
      </td>
      <td><code>… !== …</code></td>
    </tr>
    <tr>
      <td>7</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_AND"
          >Bitwise AND (&#x26;)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… &#x26; …</code></td>
    </tr>
    <tr>
      <td>6</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_XOR"
          >Bitwise XOR (^)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… ^ …</code></td>
    </tr>
    <tr>
      <td>5</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR"
          >Bitwise OR (|)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… | …</code></td>
    </tr>
    <tr>
      <td>4</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND"
          >Logical AND (&#x26;&#x26;)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… &#x26;&#x26; …</code></td>
    </tr>
    <tr>
      <td rowspan="2">3</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR"
          >Logical OR (||)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… || …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator"
          >Nullish coalescing operator (??)</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… ?? …</code></td>
    </tr>
    <tr>
      <td rowspan="21">2</td>
      <td rowspan="16">
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators#assignment_operators"
          >Assignment</a
        >
      </td>
      <td rowspan="16">right-to-left</td>
      <td><code>… = …</code></td>
    </tr>
    <tr>
      <td><code>… += …</code></td>
    </tr>
    <tr>
      <td><code>… -= …</code></td>
    </tr>
    <tr>
      <td><code>… **= …</code></td>
    </tr>
    <tr>
      <td><code>… *= …</code></td>
    </tr>
    <tr>
      <td><code>… /= …</code></td>
    </tr>
    <tr>
      <td><code>… %= …</code></td>
    </tr>
    <tr>
      <td><code>… &#x3C;&#x3C;= …</code></td>
    </tr>
    <tr>
      <td><code>… >>= …</code></td>
    </tr>
    <tr>
      <td><code>… >>>= …</code></td>
    </tr>
    <tr>
      <td><code>… &#x26;= …</code></td>
    </tr>
    <tr>
      <td><code>… ^= …</code></td>
    </tr>
    <tr>
      <td><code>… |= …</code></td>
    </tr>
    <tr>
      <td><code>… &#x26;&#x26;= …</code></td>
    </tr>
    <tr>
      <td><code>… ||= …</code></td>
    </tr>
    <tr>
      <td><code>… ??= …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator"
          >Conditional (ternary) operator</a
        >
      </td>
      <td>right-to-left<br />(Groups on expressions after <code>?</code>)</td>
      <td><code>… ? … : …</code></td>
    </tr>
    <tr>
      <td>
        <a
          href="/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions"
          >Arrow (=>)</a
        >
      </td>
      <td rowspan="4">n/a</td>
      <td><code>… => …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/yield", "yield")}}</td>
      <td><code>yield …</code></td>
    </tr>
    <tr>
      <td>{{jsxref("Operators/yield*", "yield*")}}</td>
      <td><code>yield* …</code></td>
    </tr>
    <tr>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax"
          >Spread (...)</a
        >
      </td>
      <td><code>... …</code></td>
    </tr>
    <tr>
      <td >1</td>
      <td>
        <a href="/en-US/docs/Web/JavaScript/Reference/Operators/Comma_Operator"
          >Comma / Sequence</a
        >
      </td>
      <td>left-to-right</td>
      <td><code>… , …</code></td>
    </tr>
  </tbody>
</table>