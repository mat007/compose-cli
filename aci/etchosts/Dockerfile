#   Copyright 2020 Docker Compose CLI authors

#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at

#       http://www.apache.org/licenses/LICENSE-2.0

#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.

FROM golang:1.18 AS builder
WORKDIR $GOPATH/src/github.com/docker/compose-cli/aci/etchosts
COPY . .
RUN GO111MODULE=auto CGO_ENABLED=0 go build -ldflags="-w -s" -o /go/bin/hosts main/main.go

FROM scratch
COPY --from=builder /go/bin/hosts /hosts
