---
permalink: also-bulk-merge
---

## Definition

The Dapper Plus AlsoBulkMerge method allow to MERGE entities in a database table or a view using a lambda expression.

The lambda expression use the entity or the IEnumerable<TEntity> from the last Bulk[Action] or ThenBulk[Action] chained method. (The action can be an insert, update, delete or merge operation).

## Also Bulk Merge with "One to One" Relation

The Dapper Plus AlsoBulkMerge method allow merging a related item with a "One to One" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and also the related invoice.
connection.BulkMerge(order)
          .AlsoBulkMerge(order => order.Invoice);

//Merge a list of orders and also the related invoice to every order.
connection.BulkMerge(orders)
          .AlsoBulkMerge(order => order.Invoice);
{% endhighlight %}

## Also Bulk Merge with "One to Many" Relation

The Dapper Plus AlsoBulkMerge method allow merging related items with a "One to Many" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and also all related items.
connection.BulkMerge(order)
          .AlsoBulkMerge(order => order.Items);

//Merge a list of orders and also all related items to every order.
connection.BulkMerge(orders);
          .AlsoBulkMerge(order => order.Items);
{% endhighlight %}

## Also Bulk Merge and Mixed Relation

The Dapper Plus AlsoBulkMerge method allow merging related item(s) with any relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order, also all related items and also the related invoice.
connection.BulkMerge(order)
          .AlsoBulkMerge(order => order.Items, order => order.Invoice);

//Merge a list of orders, also all related items to every order and also the related invoice to every order.
connection.BulkMerge(orders)
          .AlsoBulkMerge(order => order.Items, order => order.Invoice);
{% endhighlight %}

## Also Bulk Merge Chain Action

The Dapper Plus AlsoBulkMerge method allow chaining multiple bulk action methods.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and also all related items. Merge an invoice and also all related invoice items.
connection.BulkMerge(order)
          .AlsoBulkMerge(order => order.Items)
          .BulkMerge(invoice)
          .AlsoBulkMerge(invoice => invoice.Items);

//Merge a list of orders and also all related items to every order. Merge a list of invoices and also all related items to every invoice.
connection.BulkMerge(orders)
          .AlsoBulkMerge(order => order.Items)
          .BulkMerge(invoices)
          .AlsoBulkMerge(invoice => invoice.Items);

{% endhighlight %}

**************************
The Dapper Plus BulkMerge method allow to MERGE entities in a database table or a view.

## Bulk Merge Entity

The Dapper Plus BulkMerge method allow merging a single or multiple entities of the same type.

{% include template-example.html %} 
{% highlight csharp %}

//Merge a single order.
connection.BulkMerge(order);

//Merge multiple orders.
connection.BulkMerge(order1, order2, order3);
{% endhighlight %}

## Bulk Merge IEnumerable<TEntity>

The Dapper Plus BulkMerge method allow merging a single enumerable or multiple enumerable of entities of the same type.

{% include template-example.html %} 
{% highlight csharp %}

//Merge a list of orders.
connection.BulkMerge(orders);

//Merge multiple list of orders.
connection.BulkMerge(orders1, orders2, orders3);
{% endhighlight %}

## Bulk Merge with "One to One" Relation

The Dapper Plus BulkMerge method allow merging a related item with a "One to One" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and the related invoice.
connection.BulkMerge(order, order => order.Invoice);

//Merge a list of orders and the related invoice to every order.
connection.BulkMerge(orders, order => order.Invoice);
{% endhighlight %}

## Bulk Merge with "One to Many" Relation

The Dapper Plus BulkMerge method allow merging related items with a "One to Many" relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and all related items.
connection.BulkMerge(order, order => order.Items);

//Merge a list of orders and all related items to every order.
connection.BulkMerge(orders, order => order.Items);
{% endhighlight %}

## Bulk Merge with "Mixed" Relation

The Dapper Plus BulkMerge method allow merging related item(s) with any relation.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order, all related items, and the related invoice.
connection.BulkMerge(order, order => order.Items, order => order.Invoice);

//Merge a list of orders, all related items to every order, and the related invoice to every order.
connection.BulkMerge(orders, order => order.Items, order => order.Invoice);
{% endhighlight %}

## Bulk Merge Chain Action

The Dapper Plus BulkMerge method allow chaining multiple bulk action methods.

{% include template-example.html %} 
{% highlight csharp %}

//Merge an order and all related items. Merge an invoice and all related invoice items.
connection.BulkMerge(order, order => order.Items)
          .BulkMerge(invoice, invoice => invoice.Items);

//Merge a list of orders and all related items to every order. Merge a list of invoices and 
//all related items to every invoice.
connection.BulkMerge(orders, order => order.Items)
          .BulkMerge(invoices, invoice => invoice.Items);

{% endhighlight %}

