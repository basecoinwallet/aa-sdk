```ts
export type SendTransactionParameters<
  TChain extends Chain | undefined = Chain | undefined,
  TAccount extends Account | undefined = Account | undefined,
  TChainOverride extends Chain | undefined = Chain | undefined,
  ///
  derivedChain extends Chain | undefined = DeriveChain<TChain, TChainOverride>
> = UnionOmit<FormattedTransactionRequest<derivedChain>, "from"> &
  GetAccountParameter<TAccount> &
  GetChainParameter<TChain, TChainOverride>;
```

## Parameters

### `SendTransactionParameters`

Same as `viem` [`TransactionRequest`](https://viem.sh/docs/glossary/types#transactionrequest), but with the `from` field excluded

- `overrides?:` [`UserOperationOverrides`](/resources/types#UserOperationOverrides)

Optional parameter where you can specify override values for `maxFeePerGas`, `maxPriorityFeePerGas`, `callGasLimit`, `preVerificationGas`, `verificationGasLimit`, `paymasterAndData`, or `nonceKey` for the user operation request

- `account?: TAccount extends SmartContractAccount | undefined`

When using this action, if the `SmartContractAccount` has not been connected to the `SmartAccountClient` (e.g. `SmartAccountClient` not instantiated with your `SmartContractAccount` during [`createSmartAccountClient`](/packages/aa-core/smart-account-client/)). If the account is not connected, you can specify the `SmartContractAccount` instance to use for the function call.
