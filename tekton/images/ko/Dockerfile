# Copyright 2018 The Tekton Authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
FROM golang:1.19-alpine@sha256:31c62d91ada60d52cd2e40e1134778d32549cd58c131b30dd41069f998dc8490
LABEL maintainer "Tekton Authors <tekton-dev@googlegroups.com>"

ENV GOROOT /usr/local/go
RUN apk add --no-cache curl ca-certificates
RUN update-ca-certificates

ARG KO_VERSION=0.12.0
RUN curl -L https://github.com/google/ko/releases/download/v${KO_VERSION}/ko_${KO_VERSION}_Linux_x86_64.tar.gz > ko_${KO_VERSION}.tar.gz
RUN tar -C /usr/local/bin -xzf ko_${KO_VERSION}.tar.gz

RUN apk add --no-cache musl-dev gcc git
ENV GO111MODULE on
RUN go install sigs.k8s.io/kustomize/kustomize/v4@v4.5.7
