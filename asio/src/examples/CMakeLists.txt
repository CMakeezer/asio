if(ENABLE_CXX_11_EXAMPLES)
  function(asioExample name srcs libs std)
      add_executable(${name} ${srcs})
      target_link_libraries(${name} PRIVATE ${libs})
      target_compile_features(${name} PRIVATE ${std})
  endfunction()
  asioExample(server ${EXAMPLE_PATH}/cpp11/allocation/server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(reference_counted ${EXAMPLE_PATH}/cpp11/buffers/reference_counted.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(chat_client ${EXAMPLE_PATH}/cpp11/chat/chat_client.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(chat_server ${EXAMPLE_PATH}/cpp11/chat/chat_server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(async_tcp_echo_server ${EXAMPLE_PATH}/cpp11/echo/async_tcp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(async_udp_echo_server ${EXAMPLE_PATH}/cpp11/echo/async_udp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(blocking_tcp_echo_client ${EXAMPLE_PATH}/cpp11/echo/blocking_tcp_echo_client.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(blocking_tcp_echo_server ${EXAMPLE_PATH}/cpp11/echo/blocking_tcp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(blocking_udp_echo_client ${EXAMPLE_PATH}/cpp11/echo/blocking_udp_echo_client.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(blocking_udp_echo_server ${EXAMPLE_PATH}/cpp11/echo/blocking_udp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(actor ${EXAMPLE_PATH}/cpp11/executors/actor.cpp asio cxx_std_11)
  asioExample(bank_account_1 ${EXAMPLE_PATH}/cpp11/executors/bank_account_1.cpp asio cxx_std_11)
  asioExample(bank_account_2 ${EXAMPLE_PATH}/cpp11/executors/bank_account_2.cpp asio cxx_std_11)
  asioExample(pipeline ${EXAMPLE_PATH}/cpp11/executors/pipeline.cpp asio cxx_std_11)
  asioExample(priority_scheduler ${EXAMPLE_PATH}/cpp11/executors/priority_scheduler.cpp asio cxx_std_11)
  if(UNIX)
    asioExample(daemon ${EXAMPLE_PATH}/cpp11/fork/daemon.cpp asio cxx_std_11)
    asioExample(process_per_connection ${EXAMPLE_PATH}/cpp11/fork/process_per_connection.cpp asio cxx_std_11)
  endif()
  asioExample(daytime_client ${EXAMPLE_PATH}/cpp11/futures/daytime_client.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  #asioExample(echo_server ${EXAMPLE_PATH}/cpp11/spawn/echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_11) #boost dependency
  #asioExample(parallel_grep ${EXAMPLE_PATH}/cpp11/spawn/parallel_grep.cpp "asio;ws2_32;Mswsock" cxx_std_11) #boost dependency
  asioExample(sender ${EXAMPLE_PATH}/cpp11/multicast/sender.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  asioExample(receiver ${EXAMPLE_PATH}/cpp11/multicast/receiver.cpp "asio;ws2_32;Mswsock" cxx_std_11)
  if(UNIX)
    asioExample(connect_pair ${EXAMPLE_PATH}/cpp11/local/connect_pair.cpp asio cxx_std_11)
    asioExample(iostream_client ${EXAMPLE_PATH}/cpp11/local/iostream_client.cpp asio cxx_std_11)
    asioExample(stream_client ${EXAMPLE_PATH}/cpp11/local/stream_client.cpp asio cxx_std_11)
    asioExample(stream_server ${EXAMPLE_PATH}/cpp11/local/stream_server.cpp asio cxx_std_11)
  endif()

endif()

if(ENABLE_CXX_14_EXAMPLES)
  asioExample(actor ${EXAMPLE_PATH}/cpp14/executors/actor.cpp asio cxx_std_14)
  asioExample(async_1 ${EXAMPLE_PATH}/cpp14/executors/async_1.cpp asio cxx_std_14)
  asioExample(async_2 ${EXAMPLE_PATH}/cpp14/executors/async_2.cpp asio cxx_std_14)
  asioExample(bank_account_1 ${EXAMPLE_PATH}/cpp14/executors/bank_account_1.cpp asio cxx_std_14)
  asioExample(bank_account_2 ${EXAMPLE_PATH}/cpp14/executors/bank_account_2.cpp asio cxx_std_14)
  asioExample(pipeline ${EXAMPLE_PATH}/cpp14/executors/pipeline.cpp asio cxx_std_14)
  asioExample(priority_scheduler ${EXAMPLE_PATH}/cpp14/executors/priority_scheduler.cpp asio cxx_std_14)
  asioExample(http_client ${EXAMPLE_PATH}/cpp14/iostreams/http_client.cpp "asio;ws2_32" cxx_std_14)

  asioExample(async_tcp_echo_server ${EXAMPLE_PATH}/cpp14/echo/async_tcp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_14)
  asioExample(async_udp_echo_server ${EXAMPLE_PATH}/cpp14/echo/async_udp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_14)
  asioExample(blocking_tcp_echo_client ${EXAMPLE_PATH}/cpp14/echo/blocking_tcp_echo_client.cpp "asio;ws2_32;Mswsock" cxx_std_14)
  asioExample(blocking_tcp_echo_server ${EXAMPLE_PATH}/cpp14/echo/blocking_tcp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_14)
  asioExample(blocking_udp_echo_client ${EXAMPLE_PATH}/cpp14/echo/blocking_udp_echo_client.cpp "asio;ws2_32;Mswsock" cxx_std_14)
  asioExample(blocking_udp_echo_server ${EXAMPLE_PATH}/cpp14/echo/blocking_udp_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_14)
endif()

if(ENABLE_CXX_17_EXAMPLES)
  asioExample(chat_server ${EXAMPLE_PATH}/cpp17/coroutines_ts/chat_server.cpp "asio;ws2_32;Mswsock" cxx_std_17)
  asioExample(double_buffered_echo_server ${EXAMPLE_PATH}/cpp17/coroutines_ts/double_buffered_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_17)
  asioExample(echo_server ${EXAMPLE_PATH}/cpp17/coroutines_ts/echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_17)
  asioExample(range_based_for ${EXAMPLE_PATH}/cpp17/coroutines_ts/range_based_for.cpp "asio;ws2_32;Mswsock" cxx_std_17)
  asioExample(refactored_echo_server ${EXAMPLE_PATH}/cpp17/coroutines_ts/refactored_echo_server.cpp "asio;ws2_32;Mswsock" cxx_std_17)
endif()
