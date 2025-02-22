#  Copyright 2019 U.C. Berkeley RISE Lab
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.

CMAKE_MINIMUM_REQUIRED(VERSION 3.6 FATAL_ERROR)

SET(KVS_SOURCE
	server.cpp
	node_join_handler.cpp
  node_depart_handler.cpp
  self_depart_handler.cpp
  user_request_handler.cpp
  gossip_handler.cpp
  replication_response_handler.cpp
  replication_change_handler.cpp
  cache_ip_response_handler.cpp
  utils.cpp)

ADD_EXECUTABLE(anna-kvs ${KVS_SOURCE})
TARGET_LINK_LIBRARIES(anna-kvs anna-hash-ring ${KV_LIBRARY_DEPENDENCIES} ${PROTOBUF_LIBRARIES})
ADD_DEPENDENCIES(anna-kvs hydro-zmq zeromq zeromqcpp)
