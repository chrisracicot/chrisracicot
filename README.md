SELECT rcv_customer.first_name "First", rcv_customer.last_name "Last", rcv_tour_destination.order# "Order#", rcv_destination.price "Price"
FROM rcv_customer JOIN rcv_tour_customer USING (customer_number)
JOIN rcv_tour_destination USING (tour_code)
JOIN rcv_destination USING (dest_code)
GROUP BY CUBE (rcv_customer.first_name, rcv_customer.last_name, rcv_tour_destination.order#, rcv_destination.price)
ORDER BY 2,1;
