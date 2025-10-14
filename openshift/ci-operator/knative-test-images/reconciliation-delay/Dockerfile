# DO NOT EDIT! Generated Dockerfile for test/test_images/reconciliation-delay.
ARG GO_BUILDER=registry.ci.openshift.org/openshift/release:rhel-9-release-golang-1.23-openshift-4.19
ARG GO_RUNTIME=registry.access.redhat.com/ubi9/ubi-minimal

FROM $GO_BUILDER as builder

WORKDIR /workspace
COPY . .

ENV CGO_ENABLED=1
ENV GOEXPERIMENT=strictfipsruntime

RUN go build -tags strictfipsruntime -o /usr/bin/main ./test/test_images/reconciliation-delay

FROM $GO_RUNTIME

ARG VERSION=knative-v1.17

COPY --from=builder /usr/bin/main /ko-app/reconciliation-delay
COPY LICENSE /licenses/

USER 65532

LABEL \
      com.redhat.component="openshift-serverless-1-serving-test-test-images-reconciliation-delay-rhel9-container" \
      name="openshift-serverless-1/serving-test-test-images-reconciliation-delay-rhel9" \
      version=$VERSION \
      summary="Red Hat OpenShift Serverless 1 Serving Test Test Images Reconciliation Delay" \
      maintainer="serverless-support@redhat.com" \
      description="Red Hat OpenShift Serverless 1 Serving Test Test Images Reconciliation Delay" \
      io.k8s.display-name="Red Hat OpenShift Serverless 1 Serving Test Test Images Reconciliation Delay" \
      io.k8s.description="Red Hat OpenShift Serverless Serving Test Test Images Reconciliation Delay" \
      io.openshift.tags="test-test-images-reconciliation-delay" \
      cpe="cpe:/a:redhat:openshift_serverless:1.37::el9"

ENTRYPOINT ["/ko-app/reconciliation-delay"]
