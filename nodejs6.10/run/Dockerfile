FROM lambci/lambda-base

ENV PATH=/var/lang/bin:/usr/local/bin:/usr/bin/:/bin \
    LD_LIBRARY_PATH=/var/lang/lib:/lib64:/usr/lib64:/var/runtime:/var/runtime/lib:/var/task:/var/task/lib \
    AWS_EXECUTION_ENV=AWS_Lambda_nodejs6.10 \
    NODE_PATH=/var/runtime:/var/task:/var/runtime/node_modules

RUN rm -rf /var/runtime /var/lang && \
  curl https://lambci.s3.amazonaws.com/fs/nodejs6.10.tgz | tar -zx -C /

COPY awslambda-mock.js /var/runtime/node_modules/awslambda/build/Release/awslambda.js

USER sbx_user1051

ENTRYPOINT ["/var/lang/bin/node", "--expose-gc", "--max-executable-size=160", "--max-semi-space-size=150", "--max-old-space-size=2547", \
  "/var/runtime/node_modules/awslambda/index.js"]

