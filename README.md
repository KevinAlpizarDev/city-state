<%= form_with(model: address, class: "contents", data: {controller: "form-reset"}) do |form| %>
  <% if address.errors.any? %>
    <div id="error_explanation" class="bg-red-50 text-red-500 px-3 py-2 font-medium rounded-md mt-3">
      <h2><%= pluralize(address.errors.count, "error") %> prohibited this address from being saved:</h2>
      <ul class="list-disc ml-6">
        <% address.errors.each do |error| %>
          <li><%= error.full_message %></li>
        <% end %>
      </ul>
    </div>
  <% end %>

  <div class="my-5">
    <%= form.label :country %>
    <%= form.select :country, address.countries.invert, { include_blank: true }, class: ["block shadow-sm rounded-md border px-3 py-2 mt-2 w-full", {"border-gray-400 focus:outline-blue-600": address.errors[:country].none?, "border-red-400 focus:outline-red-600": address.errors[:country].any?}], data: { action: "change->form-element#autosubmit" } %>
  </div>

  <div class="my-5">
    <%= form.label :state %>
    <%= form.select :state, address.states.invert, { include_blank: true }, class: ["block shadow-sm rounded-md border px-3 py-2 mt-2 w-full", {"border-gray-400 focus:outline-blue-600": address.errors[:state].none?, "border-red-400 focus:outline-red-600": address.errors[:state].any?}], data: { action: "change->form-element#autosubmit" } %>
  </div>

  <div class="my-5">
    <%= form.label :city %>
    <%= form.select :city, address.cities, class: ["block shadow-sm rounded-md border px-3 py-2 mt-2 w-full", {"border-gray-400 focus:outline-blue-600": address.errors[:city].none?, "border-red-400 focus:outline-red-600": address.errors[:city].any?}] %>
  </div>

  <div class="my-5">
    <%= form.label :details %>
    <%= form.text_field :details, class: ["block shadow-sm rounded-md border px-3 py-2 mt-2 w-full", {"border-gray-400 focus:outline-blue-600": address.errors[:details].none?, "border-red-400 focus:outline-red-600": address.errors[:details].any?}] %>
  </div>

  <div class="inline">
    <%= form.submit class: "w-full sm:w-auto rounded-md px-3.5 py-2.5 bg-blue-600 hover:bg-blue-500 text-white inline-block font-medium cursor-pointer" %>
  </div>
<% end %>
